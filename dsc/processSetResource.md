---
title: Risorsa ProcessSet DSC
ms.date: 2016-05-23
keywords: powershell, DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 012a0e5c4f2a1f60ecea869d588b9c54e0567ced

---

# Risorsa WindowsProcess DSC

> Si applica a: Windows PowerShell 5.0

La risorsa **ProcessSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per configurare i processi in un nodo di destinazione. Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa WindowsProcess](windowsProcessResource.md) per ogni gruppo specificato nel parametro `GroupName`.

## Sintassi

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| Arguments| Stringa che contiene argomenti da passare al processo così come è. Se è necessario passare più argomenti, inserirli tutti in questa stringa.| 
| Path| Percorsi degli eseguibili del processo. Se questi sono i nomi dei file eseguibili (non i percorsi completi), la risorsa DSC cercherà i file nella variabile **Path** di ambiente (`$env:Path`). Se i valori di questa proprietà sono percorsi completi, DSC non userà la variabile **Path** di ambiente per individuare i file e genererà un errore se il percorso non esiste. I percorsi relativi non sono consentiti.| 
| Credential| Indica le credenziali per l'avvio del processo.| 
| Ensure| Specifica se il processo esiste. Impostare questa proprietà su "Present" per specificare che il processo esiste. In caso contrario, impostarla su "Absent". Il valore predefinito è "Present".| 
| StandardErrorPath| Percorso in cui i processi scrivono l'errore standard. Qualsiasi file esistente verrà sovrascritto.| 
| StandardInputPath| Flusso da cui il processo riceve l'input standard.| 
| StandardOutputPath| Percorso del file in cui i processi scrivono l'output standard. Qualsiasi file esistente verrà sovrascritto.| 
| WorkingDirectory| Percorso usato come directory di lavoro corrente per i processi.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **_ResourceType**, la sintassi per usare questa proprietà è 'DependsOn = "[ResourceType]ResourceName"''.| 




<!--HONumber=Jul16_HO1-->


