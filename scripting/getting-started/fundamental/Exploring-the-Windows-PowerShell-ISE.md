---
title:  Esplorazione di Windows PowerShell ISE
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
---

# Esplorazione di Windows PowerShell ISE
È possibile usare Windows PowerShell® Integrated Scripting Environment (ISE) per creare, eseguire ed eseguire il debug di script e comandi. Windows PowerShell ISE include la barra dei menu, le schede di Windows PowerShell, la barra degli strumenti, le schede degli script, un riquadro di script, un riquadro della console, una barra di stato, un dispositivo di scorrimento per le dimensioni del testo e una Guida sensibile al contesto.

> [!NOTE] A partire da Windows PowerShell ISE 3.0 i riquadri dei comandi e di output sono stati combinati in un unico riquadro della console.

## Barra dei menu
La barra dei menu contiene i menu **File**, **Modifica**, **Visualizza**, **Strumenti**, **Debug**, **Componenti aggiuntivi** e **?**. I pulsanti dei menu consentono di eseguire attività relative alla scrittura e all'esecuzione di script, nonché all'esecuzione di comandi in Windows PowerShell ISE. Nella barra dei menu può essere anche inserito uno [strumento aggiuntivo](../../core-powershell/ise/The-ISEAddOnTool-Object.md) eseguendo script che usano il [modello a oggetti di scripting di Windows PowerShell ISE](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md).

> [!NOTE] In Windows PowerShell ISE 2.0 i menu **Strumenti** e **Componenti aggiuntivi** non erano disponibili.

## Schede di Windows PowerShell
Una scheda di Windows PowerShell è l'ambiente in cui viene eseguito uno script di Windows PowerShell. È possibile aprire nuove schede di Windows PowerShell in Windows PowerShell ISE per creare ambienti distinti nel computer locale o in computer remoti. Possono essere aperte contemporaneamente al massimo otto schede di PowerShell.

## Barra degli strumenti
Nella barra degli strumenti si trovano i seguenti pulsanti.

|Pulsante|Function|
|----------|------------|
|**Nuovo**|Apre un nuovo script.|
|**Apri**|Apre uno script o un file esistente.|
|**Salva**|Salva uno script o un file.|
|**Taglia**|Taglia il testo selezionato copiandolo negli Appunti.|
|**Copiare**|Copia il testo selezionato negli appunti.|
|**Incolla**|Incolla il contenuto degli Appunti nella posizione del cursore.|
|**Cancella riquadro di output**|Cancella l'intero contenuto del riquadro di output.|
|**Annulla**|Inverte l'operazione appena eseguita.|
|**Ripeti**|Esegue l'operazione appena annullata.|
|**Esegui script**|Esegue uno script.|
|**Esegui selezione**|Esegue una parte selezionata dello script.|
|**Arresta operazione**|Arresta uno script che è in esecuzione.|
|**Scheda Nuova sessione PowerShell remota**|Crea una nuova scheda di PowerShell che stabilisce una sessione in un computer remoto. Verrà visualizzata una finestra di dialogo che richiede di immettere i dettagli necessari per stabilire la connessione remota.|
|**Avvia PowerShell.exe**|Apre una console di PowerShell.|
|**Mostra riquadro di script in alto**|Sposta il riquadro di script in alto nello schermo.|
|**Mostra riquadro di script a destra**|Sposta il riquadro di script a destra nello schermo.|
|**Mostra riquadro di script ingrandito**|Ingrandisce il riquadro di script.|

## Scheda dello script
Visualizza il nome dello script che si sta modificando. È possibile fare clic sulla scheda di uno script per selezionare lo script da modificare.

Quando si passa il puntatore sulla scheda di uno script, il percorso completo del file di script appare in una descrizione comando.

## Riquadro di script
Consente di creare ed eseguire script. È possibile aprire, modificare ed eseguire gli script esistenti nel riquadro di script.

## Riquadro di output
Visualizza i risultati dei comandi e degli script eseguiti. È inoltre possibile copiare e cancellare il contenuto del riquadro di output.

## Riquadro dei comandi
Consente di scrivere comandi. È possibile eseguire un comando di una riga o su più righe nel riquadro dei comandi. Premere MAIUSC+INVIO per immettere ogni riga di un comando su più righe e premere INVIO dopo l'ultima riga per eseguire il comando su più righe. Il prompt visualizzato nella parte superiore del riquadro dei comandi mostra il percorso della directory di lavoro corrente.

## Barra di stato
Consente di vedere se i comandi e gli script in esecuzione sono completi. La barra di stato è nella parte inferiore dello schermo. Nella barra di stato vengono visualizzate parti selezionate di messaggi di errore.

## Dispositivo di scorrimento per le dimensioni del testo
Aumenta o diminuisce le dimensioni del testo sullo schermo.

## ?
La Guida di Windows PowerShell ISE è disponibile sul Web nella libreria TechNet. È possibile aprire la Guida scegliendo **Guida di Windows PowerShell ISE** dal menu **?** o premendo F1 in un punto qualsiasi tranne quando il cursore si trova sul nome di un cmdlet nel riquadro di script o in quello della console. Dal menu **?** è anche possibile eseguire il cmdlet Update-Help e visualizzare la finestra di comando, che fornisce assistenza per la creazione di comandi visualizzando tutti i parametri di un cmdlet e consentendo di specificare i parametri in un modulo di semplice uso.

## Vedere anche
[Uso di Windows PowerShell ISE](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


