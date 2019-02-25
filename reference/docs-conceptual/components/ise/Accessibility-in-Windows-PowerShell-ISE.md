---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Accessibilità in Windows PowerShell ISE
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 78a001dbe43a0b005d10a817e05e4cc7a72f5bd0
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401410"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Accessibilità in Windows PowerShell ISE

Questo argomento descrive le funzionalità di accessibilità di Windows PowerShell Integrated Scripting Environment (ISE) che potrebbero risultare utili.

* [Come modificare le dimensioni e la posizione dei riquadri della console e di script](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Tasti di scelta rapida per la modifica del testo](#keyboard-shortcuts-for-editing-text)
* [Tasti di scelta rapida per l'esecuzione di script](#keyboard-shortcuts-for-running-scripts)
* [Tasti di scelta rapida per la personalizzazione della visualizzazione](#keyboard-shortcuts-for-customizing-the-view)
* [Tasti di scelta rapida per il debug di script](#keyboard-shortcuts-for-debugging-scripts)
* [Tasti di scelta rapida per le schede di Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Tasti di scelta rapida per avvio e uscita](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft cerca di sviluppare prodotti e servizi che siano facili da utilizzare per chiunque. Gli argomenti seguenti forniscono informazioni sulle funzionalità, i prodotti e i servizi che migliorano l'accessibilità di Windows PowerShell ISE per gli utenti disabili.

Windows PowerShell ISE supporta la modalità a contrasto elevato. Per gli utenti con problemi di vista sono disponibili informazioni sui punti di interruzione tramite i cmdlet per la gestione dei punti di interruzione, come [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) e [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Per altre informazioni, vedere 'Come gestire i punti di interruzione' in [Modalità di esecuzione del debug degli script in Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Oltre alle funzionalità e utilità di accessibilità disponibili in Microsoft Windows, le funzionalità seguenti rendono Windows PowerShell ISE più accessibile agli utenti disabili:

- Tasti di scelta rapida

- Tabella di colorazione della sintassi e la possibilità di modificare diverse altre impostazioni di colore mediante l'oggetto di scripting [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb).

- Modifica delle dimensioni del testo

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Come modificare le dimensioni e la posizione dei riquadri della console e di script

È possibile usare la procedura seguente per modificare le dimensioni e la posizione dei riquadri della console e di script Alla riapertura di Windows PowerShell ISE, le modifiche apportate a dimensioni e posizione verranno mantenute.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Per ridimensionare il riquadro di script e il riquadro della console

1. Posizionare il puntatore sulla linea di divisione tra il riquadro di script e il riquadro della console.

2. Quando il puntatore del mouse assume la forma di una freccia a due punte, trascinare il bordo per modificare le dimensioni del riquadro.

### <a name="to-move-the-script-pane-and-console-pane"></a>Per spostare il riquadro di script e il riquadro della console

Eseguire una delle operazioni seguenti:

- Per spostare Riquadro di script sopra Riquadro console, premere **CTRL+1** o sulla barra degli strumenti fare clic sull'icona **Mostra riquadro di script in alto** oppure scegliere **Mostra riquadro di script in alto** dal menu **Visualizza**.

- Per spostare il riquadro di script a destra del riquadro della console, premere **CTRL+2** o sulla barra degli strumenti fare clic sull'icona **Mostra riquadro di script a destra** oppure scegliere **Mostra riquadro di script a destra** dal menu **Visualizza**.

- Per ingrandire il riquadro di script, premere **CTRL+3** o sulla barra degli strumenti fare clic sull'icona **Mostra riquadro di script ingrandito** oppure scegliere **Mostra riquadro di script ingrandito** dal menu **Visualizza**.

- Per ingrandire il riquadro della console e nascondere il riquadro di script, all'estrema destra della riga di schede fare clic sull'icona **Nascondi riquadro di script** oppure nel menu **Visualizza** fare clic per deselezionare l'opzione di menu **Mostra riquadro di script**.

- Per visualizzare il riquadro di script quando il riquadro della console è ingrandito, all'estrema destra della riga di schede fare clic sull'icona **Mostra riquadro di script** oppure nel menu **Visualizza** fare clic per selezionare l'opzione di menu **Mostra riquadro di script**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Tasti di scelta rapida per la modifica del testo

È possibile usare i tasti di scelta rapida seguenti durante la modifica del testo.

|Azione|Tasti di scelta rapida|Posizione|
|----------|----------------------|----------|
|**Copia**|CTRL+C|Riquadro di script, Riquadro Console|
|**Taglia**|CTRL+X|Riquadro di script, Riquadro Console|
|**Trova nello script**|CTRL+F|Riquadro di script|
|**Trova successivo nello script**|F3|Riquadro di script|
|**Trova precedente nello script**|MAIUSC+F3|Riquadro di script|
|**Incolla**|CTRL+V|Riquadro di script, Riquadro Console|
|**Ripeti**|CTRL+Y|Riquadro di script, Riquadro Console|
|**Sostituisci nello script**|CTRL+H|Riquadro di script|
|**Salva**|CTRL+S|Riquadro di script|
|**Seleziona tutto**|CTRL+A|Riquadro di script, Riquadro Console|
|**Annulla**|CTRL+Z|Riquadro di script, Riquadro Console|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Tasti di scelta rapida per l'esecuzione di script

È possibile usare i tasti di scelta rapida seguenti durante l'esecuzione di script nel riquadro di script.

|Azione|Tasto di scelta rapida|
|----------|---------------------|
|**Nuovo**|CTRL+N|
|**Apri**|CTRL+O|
|**Esegui**|F5|
|**Esegui selezione**|F8|
|**Arresta esecuzione**|CTRL+INTERR È possibile usare CTRL+C quando il contesto non è ambiguo (in assenza di testo selezionato).|
|**TAB** (passaggio allo script successivo)|CTRL + TAB **Nota:** Pressione di TAB per passare allo script successivo funziona solo quando è aperta una sola scheda di PowerShell o quando sono aperte più schede di PowerShell, ma lo stato attivo si trova nel riquadro di Script.|
|**TAB** (passaggio allo script precedente)|CTRL + MAIUSC + TAB **Nota:** Scheda allo script precedente funziona quando aperta solo una scheda di PowerShell, o se sono aperte più schede di PowerShell e lo stato attivo si trova nel riquadro di Script.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Tasti di scelta rapida per la personalizzazione della visualizzazione

È possibile usare i tasti di scelta rapida seguenti per personalizzare la visualizzazione in Windows PowerShell ISE. Sono accessibili da tutti i riquadri nell'applicazione.

|Azione|Tasto di scelta rapida|
|----------|---------------------|
|**Vai a riquadro Console**|CTRL+D|
|**Vai al riquadro di script**|CTRL+I|
|**Mostra riquadro di script**|CTRL+R|
|**Nascondi riquadro di script**|CTRL+R|
||
|**Sposta riquadro di script in alto**|CTRL+1|
|**Sposta riquadro di script a destra**|CTRL+2|
|**Ingrandisci riquadro di script**|CTRL+3|
|**Zoom avanti**|CTRL+SEGNO PIÙ|
|**Zoom indietro**|CTRL+SEGNO MENO|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Tasti di scelta rapida per il debug di script

È possibile usare i tasti di scelta rapida seguenti durante il debug di script.

|Azione|Tasto di scelta rapida|Posizione|
|----------|---------------------|----------|
|**Esegui/Continua**|F5|Riquadro di script, durante il debug di uno script|
|**Esegui istruzione**|F11|Riquadro di script, durante il debug di uno script|
|**Esegui istruzione/routine**|F10|Riquadro di script, durante il debug di uno script|
|**Esci da istruzione/routine**|MAIUSC+F11|Riquadro di script, durante il debug di uno script|
|**Visualizza stack chiamate**|CTRL+MAIUSC+D|Riquadro di script, durante il debug di uno script|
|**Elenca punti di interruzione**|CTRL+MAIUSC+L|Riquadro di script, durante il debug di uno script|
|**Attiva/disattiva punto di interruzione**|F9|Riquadro di script, durante il debug di uno script|
|**Rimuovere tutti i punti di interruzione**|CTRL+MAIUSC+F9|Riquadro di script, durante il debug di uno script|
|**Arresta debugger**|MAIUSC+F5|Riquadro di script, durante il debug di uno script|

> [!NOTE]
>
> È anche possibile usare i tasti di scelta rapida progettati per la console di Windows PowerShell durante il debug degli script in Windows PowerShell ISE. Per usare questi tasti di scelta rapida, è necessario digitarli in Riquadro console e premere INVIO.

|Azione|Tasto di scelta rapida|Posizione|
|----------|---------------------|----------|
|**Continua**|C|Riquadro della console, durante il debug di uno script|
|**Esegui istruzione**|S|Riquadro della console, durante il debug di uno script|
|**Esegui istruzione/routine**|V|Riquadro della console, durante il debug di uno script|
|**Esci da istruzione/routine**|O|Riquadro della console, durante il debug di uno script|
|**Ripeti ultimo comando** (per Esegui istruzione o Esegui istruzione/routine)|INVIO|Riquadro della console, durante il debug di uno script|
|**Visualizza stack chiamate**|K|Riquadro della console, durante il debug di uno script|
|**Arresta debug**|Q|Riquadro della console, durante il debug di uno script|
|**Elenca lo script**|L|Riquadro della console, durante il debug di uno script|
|**Visualizza i comandi di debug della console**|H o ?|Riquadro della console, durante il debug di uno script|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Tasti di scelta rapida per le schede di Windows PowerShell

È possibile usare i tasti di scelta rapida seguenti durante l'uso delle schede di PowerShell.

|Azione|Tasto di scelta rapida|
|----------|---------------------|
|**Chiudi scheda di PowerShell**|CTRL+W|
|**Nuova scheda di PowerShell**|CTRL+T|
|**Scheda precedente di PowerShell**|CTRL+MAIUSC+TAB Questo tasto di scelta rapida funziona solo se non ci sono file aperti in alcuna scheda di PowerShell.|
|**Scheda successiva di Windows PowerShell**|CTRL+TAB Questo tasto di scelta rapida funziona solo se non ci sono file aperti in alcuna scheda di PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Tasti di scelta rapida per avvio e uscita

È possibile usare i tasti di scelta rapida seguenti per avviare la console di Windows PowerShell (PowerShell.exe) o per uscire da Windows PowerShell ISE.

|Azione|Tasto di scelta rapida|
|----------|---------------------|
|**Esci**|ALT+F4|
|**Avviare PowerShell.exe** (console di Windows PowerShell).|CTRL+MAIUSC+P|

## <a name="see-also"></a>Vedere anche

[Introduzione a Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)