# Risorse composite: uso di una configurazione DSC come risorsa

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

In situazioni reali, le configurazioni possono diventare lunghe e complesse, includere chiamate a molte risorse diverse e richiedere l'impostazione di un elevato numero di proprietà. Per risolvere questa complessità, è possibile usare una configurazione di Windows PowerShell DSC (Desired State Configuration) come risorsa per altre configurazioni. In questo caso si parla di risorsa composita. Una risorsa composita è una configurazione DSC che accetta parametri. I parametri della configurazione fungono da proprietà della risorsa. La configurazione viene salvata come file con un'estensione **.schema.psm1** e sostituisce sia lo schema MOF sia lo script di risorsa in una risorsa DSC tipica. Per altre informazioni sulle risorse DSC, vedere [Risorse Windows PowerShell DSC (Desired State Configuration)](resources.md).

## Creazione della risorsa composita

In questo esempio viene creata una configurazione che richiama diverse risorse esistenti per configurare le macchine virtuali. Invece di specificare i valori da impostare in blocchi di configurazione, la configurazione accetta diversi parametri che vengono quindi usati nei blocchi di configurazione.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### Salvataggio della configurazione come risorsa composita

Per usare la configurazione con parametri come risorsa DSC, salvarla in una struttura di directory come quella di qualsiasi altra risorsa basata su MOF e denominarla usando un'estensione **.schema.psm1**. Per questo esempio, il file sarà denominato **xVirtualMachine.schema.psm1**. È anche necessario creare un manifesto denominato **xVirtualMachine.psd1** che contiene la riga seguente. Si noti che questo si aggiunge a **MyDscResources.psd1**, il manifesto del modulo per tutte le risorse nella cartella **MyDscResources**.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Al termine, la struttura di cartelle deve essere simile a quella illustrata di seguito.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSC Resources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

La risorsa è ora individuabile usando il cmdlet Get-DscResource e le sue proprietà sono individuabili usando tale cmdlet oppure il completamento automatico con **CTRL+BARRA SPAZIATRICE** in Windows PowerShell ISE.

## Uso della risorsa composita

Verrà quindi creata una configurazione che chiama la risorsa composita. Questa configurazione chiama la risorsa composita xVirtualMachine per creare una macchina virtuale e quindi chiama la risorsa **xComputer** per rinominarla.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## Vedere anche
### Concetti
* [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md)
* [Introduzione a Windows PowerShell DSC (Desired State Configuration)](overview.md)
<!--HONumber=Feb16_HO4-->
