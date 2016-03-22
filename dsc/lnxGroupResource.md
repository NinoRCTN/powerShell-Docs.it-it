# Risorsa nxGroup DSC per Linux

La risorsa **nxGroup** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali in un nodo Linux.

## Sintassi

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| GroupName| Indica il nome del gruppo per cui si vuole specificare un determinato stato.| 
| Ensure| Determina se verificare l'esistenza del gruppo. Impostare questa proprietà su "Present" per specificare che il gruppo esiste. Impostarla su "Absent" per specificare che il gruppo non esiste. Il valore predefinito è "Present".| 
| Members| Specifica i membri che formano il gruppo.| 
| MembersToInclude| Indica gli utenti da specificare come membri del gruppo.| 
| MembersToExclude| Indica gli utenti da specificare come non membri del gruppo.| 
| PreferredGroupID| Imposta l'ID gruppo sul valore specificato, se possibile. Se l'ID gruppo è attualmente in uso, viene usato il successivo ID gruppo disponibile.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

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
<!--HONumber=Feb16_HO4-->
