---
title: Configurazione di un server di pull SMB DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 35ac9b38086b12fb48844c56a488854f63529e21

---

# Configurazione di un server di pull SMB DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Un server di pull [SMB](https://technet.microsoft.com/en-us/library/hh831795.aspx) DSC è una condivisione file SMB che rende disponibili i file di configurazione DSC e/o le risorse DSC ai nodi di destinazione quando tali nodi li richiedono.

Per usare un server di pull SMB per DSC, è necessario:
- Configurare una condivisione file SMB in un server che esegue PowerShell 4.0 o versione successiva
- Configurare un client che esegue PowerShell 4.0 o versione successiva per effettuare il pull da tale condivisione SMB

## Uso della la risorsa xSmbShare per creare una condivisione file SMB

Esistono diversi modi per configurare una condivisione file SMB, ma ecco come è possibile farlo tramite DSC.

### Installare la risorsa xSmbShare

Chiamare il cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) per installare il modulo **xSmbShare**.
>**Nota**: il cmdlet **Install-Module** è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0. È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186). **xSmbShare** contiene la risorsa DSC **xSmbShare**, che può essere usata per creare una condivisione file SMB.

### Creare la directory e la condivisione file

La configurazione seguente usa la risorsa [File](fileResource.md) per creare la directory per la condivisione e la risorsa **xSmbShare** per configurare la condivisione SMB:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }
        
    }
 
}
```

La configurazione crea la directory `C:\DscSmbShare` se non esiste già e quindi usa tale directory come condivisione file SMB. È necessario assegnare **FullAccess** all'account che deve scrivere o eliminare dalla condivisione file mentre **ReadAccess** ai nodi client che recupereranno i file di configurazione e/o le risorse DSC dalla condivisione, poiché, per impostazione predefinita, DSC viene eseguito come account di sistema. Il computer stesso deve pertanto avere accesso alla condivisione.


### Consentire l'accesso al file system al client di pull

L'assegnazione di **ReadAccess** a un nodo client consente a tale nodo di accedere alla condivisione SMB, ma non a file o cartelle al suo interno. È quindi necessario concedere in modo esplicito ai nodi client l'accesso alla cartella e alle sottocartelle della condivisione SMB. DSC consente tale operazione usando la risorsa **cNtfsPermissionEntry**, contenuta nel modulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0). La configurazione seguente aggiunge un blocco **cNtfsPermissionEntry** che concede l'accesso ReadAndExecute al client di pull:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }

        cNtfsPermissionEntry PermissionSet1 {
            
        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'
        
        }
 
        
    }
 
}
```

## Inserimento di configurazioni e risorse

Salvare nella condivisione SMB tutti i file MOF di configurazione e/o le risorse DSC che si vuole siano disponibili per il pull dai nodi client.

Qualsiasi file MOF di configurazione deve essere denominato _ConfigurationID.mof_, dove _ConfigurationID_ è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione. Per altre informazioni sulla configurazione di client di pull, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).

>**Nota:** se si usa un server di pull SMB, è necessario usare gli ID di configurazione. I nomi di configurazione non sono supportati per SMB.

Tutte le risorse necessarie per il client devono essere posizionate nella cartella della condivisione SMB come file `.zip` archiviati.  

## Creazione del checksum per il file MOF
Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione. Per creare un checksum, chiamare il cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). Il cmdlet accetta un parametro **Path** che specifica la cartella in cui si trova il file MOF di configurazione. Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione. Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella.

Il file di checksum deve essere presente nella stessa directory del file MOF di configurazione (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` per impostazione predefinita) e avere lo stesso nome, con estensione `.checksum`.

>**Nota**: se si modifica il file MOF di configurazione in qualsiasi modo, è necessario ricreare anche il file di checksum.

## Riconoscimenti

Un ringraziamento speciale per:

- Mike F. Robbins, i cui post sull'uso di SMB per DSC hanno aiutato a comporre il contenuto in questo argomento. Il suo blog è [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, che ha creato il modulo **cNtfsAccessControl**. L'origine per questo modulo è disponibile all'indirizzo https://github.com/SNikalaichyk/cNtfsAccessControl.

## Vedere anche
- [Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md)
- [Applicazione delle configurazioni](enactingConfigurations.md)
- [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md)

 



<!--HONumber=Jun16_HO4-->


