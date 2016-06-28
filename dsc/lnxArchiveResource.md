---
title: Risorsa nxArchive DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 2edbc1d11dfc7c84369430688a8b0d773277e864

---

# Risorsa nxArchive DSC per Linux

La risorsa **nxArchive** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (TAR) in un percorso specifico in un nodo Linux.

## Sintassi

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| SourcePath| Specifica il percorso di origine del file di archivio. Può essere un file con estensione tar, zip o tar.gz. | 
| DestinationPath| Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.| 
| Checksum| Definisce il tipo da usare per determinare se l'archivio di origine è stato aggiornato. I valori sono: "ctime", "mtime" e "md5". Il valore predefinito è "md5".| 
| Force| Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà **Force**, tali errori vengono ignorati. Il valore predefinito è **$false**.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| Ensure| Determina se verificare l'esistenza del contenuto dell'archivio in **Destination**. Impostare questa proprietà su "Present" per specificare che il contenuto esiste. Impostarla su "Absent" per specificare che il contenuto non esiste. Il valore predefinito è "Present".| 

## Esempio

L'esempio seguente mostra come usare la risorsa **nxArchive** per specificare che il contenuto di un file di archivio denominato `website.tar` esiste e viene estratto in una determinata destinazione.

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```




<!--HONumber=Jun16_HO4-->


