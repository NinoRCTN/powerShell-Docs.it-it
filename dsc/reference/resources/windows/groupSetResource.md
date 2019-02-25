---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
description: Fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.
title: Risorsa GroupSet DSC
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047712"
---
# <a name="dsc-groupset-resource"></a>Risorsa GroupSet DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **GroupSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione. Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Group](groupResource.md) per ogni gruppo specificato nel parametro `GroupName`.

Usare questa risorsa quando si vuole aggiungere e/o rimuovere lo stesso elenco di membri per più di un gruppo, rimuovere più di un gruppo o aggiungere più di un gruppo con lo stesso elenco di membri.

## <a name="syntax"></a>Sintassi

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| GroupName| Nomi dei gruppi per cui si vuole specificare un determinato stato.|
| MembersToExclude| Usare questa proprietà per rimuovere membri dall'appartenenza a gruppi esistenti. Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. In caso contrario, verrà generato un errore.|
| Credential| Le credenziali necessarie per accedere a risorse remote. **Nota**: questo account deve avere le autorizzazioni di Active Directory appropriate per aggiungere tutti gli account non locali al gruppo. In caso contrario, si verifica un errore.
| Ensure| Indica se i gruppi esistono. Impostare questa proprietà su "Absent" per specificare che i gruppi non esistono. Se la proprietà è impostata su "Present" (valore predefinito), specifica che i gruppi esistono.|
| Members| Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati. Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*. Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**. In caso contrario, verrà generato un errore.|
| MembersToInclude| Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente. Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. In caso contrario, verrà generato un errore.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"``.|

## <a name="example-1-ensuring-groups-are-present"></a>Esempio 1: I gruppi di garantire che siano presenti

L'esempio seguente illustra come assicurarsi che siano presenti due gruppi denominati "myGroup" e "myOtherGroup".

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> In questo esempio vengono usate credenziali in testo non crittografato per maggiore semplicità. Per informazioni sulla crittografia delle credenziali nel file MOF della configurazione, vedere [Protezione del file MOF](../../../pull-server/secureMOF.md).