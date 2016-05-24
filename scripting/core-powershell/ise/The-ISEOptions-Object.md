---
title: Oggetto ISEOptions
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
---
# Oggetto ISEOptions
  L'oggetto **ISEOptions** rappresenta varie impostazioni per Windows PowerShell ISE. È un'istanza della classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.

 L'oggetto **ISEOptions** fornisce i metodi e le proprietà seguenti.

 **Metodo**

-   [RestoreDefaultConsoleTokenColors()](#rdctc)

-   [RestoreDefaults()](#rd)

-   [RestoreDefaultTokenColors()](#rdtc)

-   [RestoreDefaultXmlTokenColors()](#rdxtc)

 **Proprietà**

-   [AutoSaveMinuteInterval](#asmi)

-   [CommandPaneBackgroundColor](#cpbc)

-   [CommandPaneUp](#cpu)

-   [ConsolePaneBackgroundColor](#conpbc)

-   [ConsolePaneForegroundColor](#conpfc)

-   [ConsolePaneTextBackgroundColor](#conptbc)

-   [ConsoleTokenColors](#contc)

-   [DebugBackgroundColor](#dbc)

-   [DebugForegroundColor](#dfc)

-   [DefaultOptions](#do)

-   [ErrorBackgroundColor](#ebc)

-   [ErrorForegroundColor](#efc)

-   [FontName](#fn)

-   [FontSize](#fs)

-   [IntellisenseTimeoutInSeconds](#itis)

-   [MruCount](#mc)

-   [OutputPaneBackgroundColor](#opbc)

-   [OutputPaneTextForegroundColor](#optfc)

-   [OutputPaneTextBackgroundColor](#optbc)

-   [ScriptPaneBackgroundColor](#spbc)

-   [ScriptPaneForegroundColor](#spfc)

-   [SelectedScriptPaneState](#ssps)

-   [ShowDefaultSnippets](#sds)

-   [ShowIntellisenseInConsolePane](#siicp)

-   [ShowIntellisenseInScriptPane](#siisp)

-   [ShowLineNumbers](#sln)

-   [ShowOutlining](#so)

-   [ShowToolBar](#stb)

-   [ShowWarningBeforeSavingOnRun](#swbsor)

-   [ShowWarningForDuplicateFiles](#swfdf)

-   [TokenColors](#tc)

-   [UseEnterToSelectInConsolePaneIntellisense](#uetsicpi)

-   [UseEnterToSelectInScriptPaneIntellisense](#uetsispi)

-   [UseLocalHelp](#ulh)

-   [VerboseBackgroundColor](#vbc)

-   [VerboseForegroundColor](#vfc)

-   [WarningBackgroundColor](#wbc)

-   [WarningForegroundColor](#wfc)

-   [XmlTokenColors](#xtc)

-   [Zoom](#z)

## Metodo

###  <a name="rdctc"></a> RestoreDefaultConsoleTokenColors()
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Ripristina i valori predefiniti dei colori dei token nel riquadro della console.

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <a name="rd"></a> RestoreDefaults()
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Ripristina i valori predefiniti di tutte le impostazioni delle opzioni nel riquadro della console. Reimposta anche il comportamento di vari messaggi di avviso che forniscono la casella di controllo standard per impedire che il messaggio venga visualizzato nuovamente.

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <a name="rdtc"></a> RestoreDefaultTokenColors()
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Ripristina i valori predefiniti dei colori dei token nel riquadro di script.

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <a name="rdxtc"></a> RestoreDefaultXmlTokenColors()
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Ripristina i valori predefiniti dei colori dei token per gli elementi XML che vengono visualizzati in Windows PowerShell ISE. Vedere anche [XmlTokenColors](#xtc).

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## Proprietà

###  <a name="asmi"></a> AutoSaveMinuteInterval
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica il numero di minuti tra le operazioni di salvataggio automatico dei file con Windows PowerShell ISE. Il valore predefinito è 2 minuti. Il valore è un numero intero.

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <a name="cpbc"></a> CommandPaneBackgroundColor
  Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.  Per le versioni successive, vedere [ConsolePaneBackgroundColor](#conpbc)..

 Specifica il colore di sfondo per il riquadro dei comandi. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <a name="cpu"></a> CommandPaneUp
  Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.

 Specifica se il riquadro dei comandi si trova sopra il riquadro di output.

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <a name="conpbc"></a> ConsolePaneBackgroundColor
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica il colore di sfondo per il riquadro della console. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <a name="conpfc"></a> ConsolePaneForegroundColor
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica il colore primo piano del testo nel riquadro della console.

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <a name="conptbc"></a> ConsolePaneTextBackgroundColor
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica il colore di sfondo del testo nel riquadro della console.

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <a name="contc"></a> ConsoleTokenColors
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica i colori dei token di IntelliSense nel riquadro della console di Windows PowerShell ISE. Questa proprietà è un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il riquadro della console. Per modificare i colori dei token di IntelliSense nel riquadro di script, vedere [TokenColors](#tc). Per reimpostare i colori ai valori predefiniti, vedere [RestoreDefaultConsoleTokenColors()](#rdctc). I colori dei token possono essere impostati per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <a name="dbc"></a> DebugBackgroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore di sfondo del testo di debug visualizzato nel riquadro della console. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <a name="dfc"></a> DebugForegroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore primo piano del testo di debug visualizzato nel riquadro della console. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <a name="do"></a> DefaultOptions
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Raccolta di proprietà che specificano i valori predefiniti da usare quando vengono usati i metodi di reimpostazione.

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3

```

###  <a name="ebc"></a> ErrorBackgroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore di sfondo del testo di errore visualizzato nel riquadro della console. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <a name="efc"></a> ErrorForegroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore primo piano del testo di errore visualizzato nel riquadro della console. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <a name="fn"></a> FontName
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il nome del tipo di carattere attualmente in uso nel riquadro di script e nel riquadro della console.

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <a name="fs"></a> FontSize
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica le dimensioni del carattere come numero intero. Viene usato nel riquadro di script, nel riquadro dei comandi e nel riquadro di output. L'intervallo di valori valido è da 8 a 32.

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <a name="itis"></a> IntellisenseTimeoutInSeconds
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica il numero di secondi durante cui IntelliSense prova a risolvere il testo attualmente digitato. Dopo questo intervallo, IntelliSense raggiunge il timeout e consente di continuare la digitazione. Il valore predefinito è 3 secondi. Il valore è un numero intero.

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <a name="mc"></a> MruCount
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica il numero di file aperti di recente che Windows PowerShell ISE registra e visualizza alla fine del menu **Apri**. Il valore predefinito è 10. Il valore è un numero intero.

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <a name="opbc"></a> OutputPaneBackgroundColor
  Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.  Per le versioni successive, vedere [ConsolePaneBackgroundColor](#conpbc)..

 Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per il riquadro di output. È un'istanza della classe **System.Windows.Media.Color**.

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <a name="optfc"></a> OutputPaneTextForegroundColor
  Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.  Per le versioni successive, vedere [ConsolePaneForegroundColor](#conpfc)..

 Proprietà di lettura/scrittura che modifica il colore primo piano del testo nel riquadro di output in Windows PowerShell ISE 2.0.

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <a name="optbc"></a> OutputPaneTextBackgroundColor
  Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.  Per le versioni successive, vedere [ConsolePaneTextBackgroundColor](#conptbc)..

 Proprietà di lettura/scrittura che modifica il colore di sfondo del testo nel riquadro di output.

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <a name="spbc"></a> ScriptPaneBackgroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per i file. È un'istanza della classe **System.Windows.Media.Color**.

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <a name="spfc"></a> ScriptPaneForegroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Proprietà di lettura/scrittura che ottiene o imposta il colore primo piano per i file non script nel riquadro di script.
Per impostare il colore primo piano per i file di script, usare la proprietà [TokenColors](The-ISEOptions-Object.md#tc).

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <a name="ssps"></a> SelectedScriptPaneState
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Proprietà di lettura/scrittura che ottiene o imposta la posizione del riquadro di script nella visualizzazione. La stringa può essere "Maximized", "Top" o "Right".

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <a name="sds"></a> ShowDefaultSnippets
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se l'elenco di frammenti di codice di **CTRL+J** comprende il set iniziale incluso in Windows PowerShell. Se è impostato su **$false**, vengono visualizzati solo i frammenti di codice definiti dall'utente nell'elenco **CTRL+J**. Il valore predefinito è **$true**..

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <a name="siicp"></a> ShowIntellisenseInConsolePane
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se IntelliSense offre suggerimenti relativi a sintassi, parametri e valori nel riquadro della console. Il valore predefinito è **$true**..

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <a name="siisp"></a> ShowIntellisenseInScriptPane
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se IntelliSense offre suggerimenti relativi a sintassi, parametri e valori nel riquadro di script. Il valore predefinito è **$true**..

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <a name="sln"></a> ShowLineNumbers
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se il riquadro di script visualizza i numeri di riga nel margine sinistro. Il valore predefinito è **$true**..

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <a name="so"></a> ShowOutlining
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se il riquadro di script visualizza le parentesi espandibili e comprimibili accanto alle sezioni di codice nel margine sinistro. Quando sono visualizzate, è possibile fare clic sull'icona del segno meno (-) accanto a un blocco di testo per comprimerlo o sull'icona del segno più (+) per espanderlo. Il valore predefinito è **$true**..

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <a name="stb"></a> ShowToolBar
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica se la barra degli strumenti ISE viene visualizzata nella parte superiore della finestra di Windows PowerShell ISE. Il valore predefinito è **$true**..

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <a name="swbsor"></a> ShowWarningBeforeSavingOnRun
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica se viene visualizzato un messaggio di avviso quando uno script viene salvato automaticamente prima di essere eseguito. Il valore predefinito è **$true**..

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <a name="swfdf"></a> ShowWarningForDuplicateFiles
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica se viene visualizzato un messaggio di avviso quando lo stesso file viene aperto in diverse schede di PowerShell. Se è impostato su **$true**, quando si apre lo stesso file in più schede, viene visualizzato il messaggio: "Una copia del file è aperta in un'altra scheda di PowerShell. Le modifiche apportate al file interesseranno tutte le copie aperte". Il valore predefinito è **$true**..

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <a name="tc"></a> TokenColors
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica i colori dei token di IntelliSense nel riquadro di script di Windows PowerShell ISE. Questa proprietà è un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il riquadro di script. Per modificare i colori dei token di IntelliSense nel riquadro della console, vedere [ConsoleTokenColors](#contc). Per reimpostare i colori ai valori predefiniti, vedere [RestoreDefaultTokenColors()](#rdtc). I colori dei token possono essere impostati per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se è possibile usare INVIO per selezionare un'opzione fornita da IntelliSense nel riquadro della console. Il valore predefinito è **$true**..

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se è possibile usare INVIO per selezionare un'opzione fornita da IntelliSense nel riquadro di script. Il valore predefinito è **$true**..

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <a name="ulh"></a> UseLocalHelp
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica se la Guida installata in locale o la Guida della libreria TechNet online viene visualizzata quando si preme F1 con il cursore posizionato su una parola chiave. Se è impostato su **$true**, una finestra popup visualizza il contenuto della Guida installata in locale. È possibile installare i file della Guida con il comando `Update-Help`. Se è impostato su **$false**, il browser apre una pagina della libreria TechNet.

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <a name="vbc"></a> VerboseBackgroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore di sfondo del testo dettagliato visualizzato nel riquadro della console. È un oggetto **System.Windows.Media.Color**.

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <a name="vfc"></a> VerboseForegroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore primo piano del testo dettagliato visualizzato nel riquadro della console. È un oggetto **System.Windows.Media.Color**.

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <a name="wbc"></a> WarningBackgroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore di sfondo del testo di avviso visualizzato nel riquadro della console. È un oggetto **System.Windows.Media.Color**.

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <a name="wfc"></a> WarningForegroundColor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive.

 Specifica il colore primo piano del testo di avviso visualizzato nel riquadro di output. È un oggetto **System.Windows.Media.Color**.

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <a name="xtc"></a> XmlTokenColors
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il contenuto XML visualizzato in Windows PowerShell ISE. I colori dei token possono essere impostati per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable. Vedere anche [RestoreDefaultXmlTokenColors()](#rdxtc)..

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <a name="z"></a> Zoom
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Specifica le dimensioni relative del testo nei riquadri della console e di script. Il valore predefinito è 100. Se si specificano valori inferiori o superiori, il testo in Windows PowerShell ISE risulta rimpicciolito o ingrandito. Il valore è un numero intero compreso tra 20 e 400.

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## Vedere anche
 [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)


<!--HONumber=May16_HO2-->


