---
title: Risorsa nxUser DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 7813185313845b74e2a37dfa4ec6bb109f32f0eb

---

# Risorsa nxUser DSC per Linux

La risorsa **nxUser** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli utenti locali in un nodo Linux.

## Sintassi

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ Mode = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Proprietà

|  Proprietà |  Indica il nome dell'account per cui si vuole specificare un determinato stato. | 
|---|---|
| UserName| Indica il percorso in cui si vuole specificare lo stato di un file o una directory.| 
| Ensure| Specifica se l'account esiste. Impostare questa proprietà su "Present" per specificare che l'account esiste e su "Absent" per specificare che non esiste.| 
| FullName| Stringa che contiene il nome completo da usare per l'account utente.| 
| Descrizione| Descrizione dell'account utente.| 
| Password| Hash della password dell'utente nel formato appropriato per il computer Linux. In genere, è un hash salt SHA-256 o SHA-512. In Debian e Ubuntu Linux, questo valore può essere generato con il comando mkpasswd. Per altre distribuzioni Linux, è possibile usare il metodo di crittografia della libreria Crypt di Python per generare l'hash.| 
| Disabled| Indica se l'account è abilitato. Impostare questa proprietà su **$true** per specificare che l'account è disabilitato e su **$false** per specificare che è abilitato.| 
| PasswordChangeRequired| Indica se l'utente può modificare la password. Impostare questa proprietà su **$true** per impedire all'utente di modificare la password e su **$false** per consentire all'utente di modificare la password. Il valore predefinito è **$false**. Questa proprietà viene valutata solo se l'account utente non esisteva in precedenza e viene creato ora.| 
| HomeDirectory| Home directory per l'utente.| 
| GroupID| ID gruppo primario per l'utente.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è "ResourceName" e il tipo è "ResourceType", la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

## Esempio

L'esempio seguente specifica che l'utente "monuser" esiste ed è un membro del gruppo "DBusers".

```
Import-DSCResource -Module nx 

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```




<!--HONumber=Jun16_HO4-->


