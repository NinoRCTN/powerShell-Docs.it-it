# Uso dello strumento di progettazione risorse

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Lo strumento di progettazione risorse è un set di cmdlet esposti dal modulo **xDscResourceDesigner** che semplifica la creazione di risorse Windows PowerShell DSC (Desired State Configuration). I cmdlet in questa risorsa offrono supporto per creare lo schema MOF, il modulo di script e la struttura di directory per la nuova risorsa. Per altre informazioni sulle risorse DSC, vedere [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md).
In questo argomento verrà creata una risorsa DSC che gestisce gli utenti di Active Directory.
Usare il cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) per installare il modulo **xDscResourceDesigner**.

>**Nota**: il cmdlet **Install-Module** è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0. È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## Creazione delle proprietà della risorsa
La prima cosa da fare è stabilire le proprietà che la risorsa dovrà esporre. In questo esempio verrà definito un utente di Active Directory con le proprietà seguenti.
 
Nome parametro e descrizione
* **UserName**: proprietà chiave che identifica in modo univoco un utente.
* **Ensure**: specifica se l'account utente deve essere presente o assente. Questo parametro avrà solo due valori possibili.
* **DomainCredential**: password di dominio per l'utente.
* **Password**: password desiderata per l'utente in modo da consentire a una configurazione di modificare la password utente, se necessario.

Per creare le proprietà, viene usato il cmdlet **New-xDscResourceProperty**. I comandi di PowerShell seguenti creano le proprietà descritte in precedenza.

```powershell
PS C:\> $UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
PS C:\> $Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
PS C:\> $DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
PS C:\> $Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## Creazione della risorsa

Dopo aver creato le proprietà della risorsa, è possibile chiamare il cmdlet **New-xDscResource** per creare la risorsa. Il cmdlet **New-xDscResource** accetta l'elenco di proprietà come parametri. Accetta anche il percorso in cui deve essere creato il modulo, il nome della nuova risorsa e il nome del modulo in cui è contenuta. Il comando di PowerShell seguente consente di creare la risorsa.

```powershell
PS C:\> New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

Il cmdlet **New-xDscResource** crea lo schema MOF, uno script di risorsa di base, la struttura di directory necessaria per la nuova risorsa e un manifesto per il modulo che espone la nuova risorsa.

Il file di schema MOF si trova in **C:\Programmi\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof** e il suo contenuto è il seguente.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
[Key] string UserName;
[Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
[Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
[Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

Lo script di risorsa si trova in **C:\Programmi\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Non include la logica effettiva per implementare la risorsa, che è necessario aggiungere manualmente. Il contenuto dello script di base è il seguente.

```powershell
function Get-TargetResource
{
[CmdletBinding()]
[OutputType([System.Collections.Hashtable])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$returnValue = @{
UserName = [System.String]
Ensure = [System.String]
DomainAdminCredential = [System.Management.Automation.PSCredential]
Password = [System.Management.Automation.PSCredential]
}

$returnValue
#>
}


function Set-TargetResource
{
[CmdletBinding()]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."

#Include this line if the resource requires a system reboot.
#$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$result = [System.Boolean]

$result
#>
}


Export-ModuleMember -Function *-TargetResource
```

## Aggiornamento della risorsa

Se è necessario aggiungere o modificare l'elenco di parametri della risorsa, è possibile chiamare il cmdlet **Update-xDscResource**. Il cmdlet aggiorna la risorsa con un nuovo elenco di parametri. Se la logica è già stata aggiunta allo script di risorsa, non viene apportata alcuna modifica.

Si supponga, ad esempio, di voler includere l'ora dell'ultimo accesso per l'utente alla risorsa. Invece che scrivere di nuovo la risorsa completamente, è possibile chiamare **New-xDscResourceProperty** per creare la nuova proprietà e quindi chiamare **Update-xDscResource** e aggiungere la nuova proprietà all'elenco di proprietà.

```powershell
PS C:\> $lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
PS C:\> Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## Test di uno schema di risorse

Lo strumento di progettazione risorse espone un altro cmdlet che è possibile usare per testare la validità di uno schema MOF scritto manualmente. Chiamare il cmdlet **Test-xDscSchema**, passando il percorso di uno schema di risorsa MOF come parametro. L'output del cmdlet conterrà eventuali errori presenti nello schema.

### Vedere anche

#### Concetti
[Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md)

#### Risorse aggiuntive
[Modulo xDscResourceDesigner](https://powershellgallery.com/packages/xDscResourceDesigner)
<!--HONumber=Feb16_HO4-->
