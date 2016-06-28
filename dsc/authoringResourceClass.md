---
title: Scrittura di una risorsa DSC personalizzata con classi di PowerShell
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 553ef07e42a4c41e5f0dc9e80c54f828d9c625c3

---

# Scrittura di una risorsa DSC personalizzata con classi di PowerShell

> Si applica a: Windows PowerShell 5.0

Con l'introduzione delle classi di PowerShell in Windows PowerShell 5.0, è ora possibile definire una risorsa DSC creando una classe. La classe definisce sia lo schema sia l'implementazione della risorsa, quindi non è necessario creare un file MOF distinto. La struttura di cartelle per una risorsa basata su classi è inoltre più semplice, perché non è necessaria una cartella **DSCResources**.

In una risorsa DSC basata su classi, lo schema viene definito come proprietà della classe che è possibile modificare con attributi per specificare il tipo di proprietà. La risorsa è implementata dai metodi **Get()**, **Set()** e **Test()** (equivalenti alle funzioni **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** in una risorsa script.

In questo argomento verrà creata una risorsa semplice denominata **FileResource** che gestisce un file in un percorso specificato.

Per altre informazioni sulle risorse DSC, vedere [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md).

## Struttura di cartelle per una risorsa basata su classi

Per implementare una risorsa DSC personalizzata con una classe di PowerShell, creare la struttura di cartelle seguente. La classe è definita in **MyDscResource.psm1** e il manifesto del modulo è definito in **MyDscResource.psd1**.

```
$env: psmodulepath (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## Creare la classe

Per creare una classe di PowerShell, usare la parola chiave class. Per specificare che una classe è una risorsa DSC, usare l'attributo **DscResource()**. Il nome della classe è il nome della risorsa DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### Dichiarare le proprietà

Lo schema della risorsa DSC viene definito come proprietà della classe. Vengono dichiarate tre proprietà, come indicato di seguito.

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

Si noti che le proprietà sono modificate dagli attributi. Il significato degli attributi è il seguente:

- **DscProperty(Key)**: la proprietà è obbligatoria. La proprietà è una chiave. I valori di tutte le proprietà contrassegnate come chiavi devono essere combinati per identificare in modo univoco un'istanza di risorsa all'interno di una configurazione.
- **DscProperty(Mandatory)**: la proprietà è obbligatoria.
- **DscProperty(NotConfigurable)**: la proprietà è di sola lettura. Le proprietà contrassegnate con questo attributo non possono essere impostate da una configurazione, ma vengono popolate dal metodo **Get()**, quando presente.
- **DscProperty()**: la proprietà è configurabile, ma non è obbligatoria.

Le proprietà **$Path** e **$SourcePath** sono entrambe stringhe. **$CreationTime** è una proprietà [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx). La proprietà **$Ensure** è un tipo di enumerazione, definito come segue.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### Implementare i metodi

I metodi **Get()**, **Set()** e **Test()** sono analoghi alle funzioni **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** in una risorsa script.

Questo codice include anche la funzione CopyFile(), una funzione helper che copia il file da **$SourcePath** a **$Path**. 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### File completo
Il file di classe completo è illustrato di seguito.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## Creare un manifesto

Per rendere disponibile una risorsa basata su classi per il motore DSC, è necessario includere un'istruzione **DscResourcesToExport** nel file manifesto per indicare al modulo di esportare la risorsa. Il manifesto è simile al seguente:

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## Testare la risorsa

Dopo aver salvato i file di classe e manifesto nella struttura di cartelle come descritto in precedenza, è possibile creare una configurazione che usa la nuova risorsa. Per informazioni su come eseguire una configurazione DSC, vedere [Applicazione delle configurazioni](enactingConfigurations.md). La configurazione seguente controlla se il file in `c:\test\test.txt` esiste e, in caso contrario, copia il file da `c:\test.txt` (è necessario creare `c:\test.txt` prima di eseguire la configurazione).

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## Vedere anche
### Concetti
[Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md)




<!--HONumber=Jun16_HO4-->


