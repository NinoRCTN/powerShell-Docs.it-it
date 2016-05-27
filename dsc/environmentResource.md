---
title:   Risorsa Environment DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Risorsa Environment DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa __Environment__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema.

## Sintassi
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| Name| Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.| 
| Ensure| Indica se una variabile esiste. Impostare questa proprietà su __Present__ per creare una variabile di ambiente se non esiste o per specificare che il suo valore corrisponde a quello fornito tramite la proprietà __Value__ se la variabile esiste già. Impostarla su __Absent__ per eliminare la variabile, se esiste.| 
| Path| Definisce la variabile di ambiente configurata. Impostare questa proprietà su __$true__ se la variabile è __Path__; in caso contrario, impostarla su __$false__. Il valore predefinito è __$false__. Se la variabile configurata è __Path__, il valore specificato tramite la proprietà __Value__ viene aggiunto al valore esistente.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| Value| Valore da assegnare alla variabile di ambiente.| 

## Esempio

L'esempio seguente specifica che __TestEnvironmentVariable__ è presente e ha il valore __TestValue__. Se la variabile non è presente, viene creata.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```



<!--HONumber=May16_HO3-->


