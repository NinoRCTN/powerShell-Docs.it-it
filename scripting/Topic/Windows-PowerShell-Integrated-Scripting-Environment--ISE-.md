---
title: Windows PowerShell Integrated Scripting Environment (ISE)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
---
# Windows PowerShell Integrated Scripting Environment (ISE)
Windows PowerShell Integrated Scripting Environment (ISE) è uno dei due host per il motore e il linguaggio di Windows PowerShell. È possibile usarlo per scrivere, eseguire e testare script in modi non disponibili nella console di Windows PowerShell. ISE aggiunge la colorazione della sintassi, il completamento tramite TAB, IntelliSense, il debug visivo e la Guida sensibile al contesto.

Con ISE è possibile eseguire i comandi in un riquadro della console, ma sono supportati anche riquadri che consentono di visualizzare contemporaneamente il codice sorgente dello script e altri strumenti integrabili in ISE. È anche possibile aprire più finestre di script contemporaneamente, opzione particolarmente utile quando si esegue il debug di uno script che usa funzioni definite in altri script o moduli.

## <a name="BKMK_NEW"></a>Novità
Ecco alcune delle funzionalità che sono state aggiunte in ISE nelle versioni più recenti di PowerShell.

### Aggiunta in PowerShell 3.0 (Windows Server 2012, Windows 8)
**IntelliSense** consente di completare automaticamente i comandi visualizzando menu di cmdlet, parametri, valori di parametri, file o cartelle corrispondenti durante la digitazione.

**Frammenti di codice**, ovvero brevi sezioni di codice che è possibile inserire facilmente negli script durante la scrittura. È disponibile una raccolta predefinita di utili frammenti di codice ed è possibile aggiungerne altri tramite il cmdlet **New-Snippet**.

È possibile creare **strumenti aggiuntivi** per aggiungere funzionalità a ISE scrivendo codice che interagisce con il [modello a oggetti di scripting di Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819478.aspx). Questi strumenti possono visualizzare i controlli in un riquadro a schede o funzionare in modo invisibile in background. Il componente aggiuntivo **Comandi** è un buon esempio incluso nella versione 3.0 e successive, che consente di visualizzare un elenco di comandi disponibili e la rispettiva Guida.

Le funzionalità **Gestione riavvio e salvataggio automatico** salvano automaticamente gli script ogni due minuti per evitare di perdere il lavoro in caso di arresto anomalo o un riavvio imprevisto.

L'**elenco degli elementi usati di recente** fa ora parte del menu Apri File in modo da facilitare l'accesso ai file usati più frequentemente.

**Riquadro della console unito**. Nelle versioni precedenti di ISE sono disponibili riquadri separati per i comandi e l'output. Questi riquadri sono ora riuniti in un unico riquadro che riproduce in modo più fedele la visualizzazione disponibile nella console di Windows PowerShell.

**Opzioni della riga di comando** Diverse nuove opzioni della riga di comando offrono maggiore controllo sul funzionamento di ISE. -NoProfile avvia ISE senza eseguire un profilo di script. -Help apre una finestra della Guida con ISE. -mta avvia ISE in "modalità apartment a thread multipli". L'impostazione predefinita è la modalità apartment a thread singolo.

**Nuove funzionalità dell'editor** rendono più semplice creare e leggere il codice:

-   **Colorazione della sintassi XML**. L'editor ISE ora applica colori alla sintassi XML nello stesso modo usato per la sintassi del codice di Windows PowerShell.

-   **Corrispondenza delle parentesi graffe**. [!INCLUDE[ise_2](../Token/ise_2_md.md)] evidenzia le parentesi graffe corrispondenti per facilitare il controllo della presenza del numero corretto di parentesi graffe di chiusura corrispondenti a quelle di apertura. È possibile usare CTRL+[ per individuare la parentesi graffa di chiusura corrispondente a quella di apertura su cui si trova il cursore.

-   **Visualizzazione struttura**. È possibile comprimere o espandere sezioni del codice facendo clic sul segno più e meno nel margine sinistro. In questo modo è più semplice trovare il codice che si sta cercando in uno script lungo.

-   **Modifica del testo con trascinamento della selezione**. È possibile selezionare un blocco di testo e trascinarlo in un'altra posizione per spostarlo. Se si tiene premuto il tasto CTRL mentre si trascina il testo selezionato, si esegue una copia anziché uno spostamento.

-   **Visualizzazione degli errori di analisi**. Windows PowerShell esamina lo script durante la digitazione. Se viene rilevato un errore, verrà visualizzata una sottolineatura ondulata rossa sotto il codice che causa l'errore. Quando si passa il mouse sull'errore indicato, il problema rilevato viene indicato in una descrizione comando.

-   **Zoom**. È possibile ingrandire il testo per facilitarne la lettura o ridurlo per ottenere un quadro d'insieme usando il dispositivo di scorrimento nell'angolo in basso a destra della finestra di ISE.

-   **Operazioni di copia e incolla di testo formattato**. Quando si esegue una copia negli Appunti da ISE vengono incluse le informazioni relative a tipo di carattere, dimensioni e colore del testo selezionato.

-   **Selezione di blocchi**. È possibile selezionare una parte di testo a forma di blocco tenendo premuto ALT mentre si seleziona il testo nel riquadro di script con il mouse oppure premendo **ALT+MAIUSC+FRECCIA**.

### Aggiunta in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)
L'ambiente ISE è stato introdotto in PowerShell 2.0.

## Requisiti per l'esecuzione di Windows PowerShell ISE
ISE è disponibile in qualsiasi computer che supporta l'esecuzione di Windows PowerShell 2.0 o versione successiva. Ogni versione di Windows e Windows Server include una versione di Windows PowerShell e ISE, ma è possibile eseguire l'aggiornamento alla versione più recente disponibile tramite l'installazione di Windows Management Framework. Eseguire questa ricerca per trovare l'ultima versione disponibile: [Download](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending). Si noti che tutte le voci con etichetta "Preview" rappresentano codice preliminare e non includono funzionalità complete.

> [!NOTE]
> Poiché [!INCLUDE[ise_2](../Token/ise_2_md.md)] richiede un'interfaccia utente grafica, non è disponibile nell'opzione di installazione dei componenti di base del server di Windows Server.

## <a name="BKMK_LINKS"></a>Vedere anche
[Uso di Windows PowerShell ISE (Integrated Scripting Environment)](http://technet.microsoft.com/library/cc732148.aspx)



<!--HONumber=Apr16_HO2-->


