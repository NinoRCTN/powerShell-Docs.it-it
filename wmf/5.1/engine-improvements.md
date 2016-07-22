---
title: Miglioramenti apportati al motore di PowerShell in WMF 5.1 (anteprima)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 0e876b291075458a089c8a550bcee84b6e06b393

---

#Miglioramenti apportati al motore PowerShell

I miglioramenti seguenti apportati al motore di PowerShell principale sono stati implementati in WMF 5.1:


## Prestazioni ##

Le prestazioni sono migliorate in alcune aree importanti:

- Avvio
- Pipelining ai cmdlet quali ForEach-Object e Where-Object più veloce del 50% circa 

Alcuni miglioramenti di esempio (i risultati possono variare in base all'hardware): 

| Scenario | 5.0 - Tempo (ms) | 5.1 - Tempo (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Prima esecuzione di PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Cache di analisi del comando integrata: `powershell -command "Unknown-Command"` | 7000 | 520 |
| '1..1000000 | % { }' | 1400 | 750 |
  
> [!NOTE]  
> Una modifica correlata all'avvio può avere impatto su alcuni scenari non supportati. PowerShell non legge i file `$pshome\*.ps1xml`: questi file sono stati convertiti in C# per evitare il sovraccarico dell'elaborazione di file XML da parte di alcuni file e della CPU. I file supportano ancora V2 side-by-side, pertanto se si modifica il contenuto del file, la modifica non avrà alcun impatto su V5, ma solo su V2. Si noti che la modifica dei contenuti di questi file non ha mai costituito uno scenario supportato.

Un'altra modifica evidente riguarda la modalità di memorizzazione nella cache dei comandi esportati e di altre informazioni relative ai moduli installati in un sistema da parte di PowerShell. In precedenza, la cache veniva archiviata nella directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. In WMF 5.1, la cache è un singolo file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Per altre informazioni dettagliate, vedere [analysis_cache.md]().


<!--HONumber=Jul16_HO3-->


