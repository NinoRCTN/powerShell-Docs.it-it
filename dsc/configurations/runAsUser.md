---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Usare credenziali con risorse DSC
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681572"
---
# <a name="use-credentials-with-dsc-resources"></a>Usare credenziali con risorse DSC

> Si applica a: Windows PowerShell 5.0, Windows PowerShell 5.1

È possibile eseguire una risorsa DSC con un set di credenziali specificato usando la proprietà **PsDscRunAsCredential** nella configurazione.
Per impostazione predefinita, DSC esegue ogni risorsa come account di sistema.
In alcuni casi può essere necessario eseguirla con le credenziali di un utente, ad esempio quando si installano pacchetti MSI in un contesto utente specifico, si impostano le chiavi del Registro di sistema di un utente, si accede a una directory locale specifica dell'utente o si accede a una condivisione di rete.

Ogni risorsa DSC ha una proprietà **PsDscRunAsCredential** che può essere impostare su qualsiasi credenziale utente (oggetto [PSCredential](/dotnet/api/system.management.automation.pscredential)).
Le credenziali possono essere hardcoded come il valore della proprietà nella configurazione oppure è possibile impostare il valore su [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), che chiederà all'utente le credenziali in fase di compilazione della configurazione. Per informazioni sulla compilazione di configurazioni, vedere [Configurazioni DSC](configurations.md).

> [!NOTE]
> In PowerShell 5.0 non è supportato l'uso della proprietà **PsDscRunAsCredential** nelle configurazioni che chiamano risorse composite.
> In PowerShell 5.1 la proprietà **PsDscRunAsCredential** è supportata nelle configurazioni che chiamano risorse composite.
> La proprietà **PsDscRunAsCredential** non è disponibile in PowerShell 4.0.

Nell'esempio seguente `Get-Credential` viene usato per richiedere le credenziali all'utente.
La risorsa **Registry** viene usata per modificare la chiave del Registro di sistema che specifica il colore di sfondo della finestra del prompt dei comandi di Windows.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> In questo esempio si presuppone che sia disponibile un certificato valido in `C:\publicKeys\targetNode.cer` e che l'identificazione personale del certificato sia il valore visualizzato.
> Per informazioni sulla crittografia delle credenziali nei file MOF della configurazione DSC, vedere [Protezione del file MOF](../pull-server/secureMOF.md).