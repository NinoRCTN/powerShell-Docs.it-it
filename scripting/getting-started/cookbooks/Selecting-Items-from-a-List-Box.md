---
title:  Selezione di elementi di una casella di riepilogo
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  327c7cc5-21d0-4ace-b151-aa1491d1d3c2
---

# Selezione di elementi di una casella di riepilogo
Usare Windows PowerShell 3.0 e versioni successive per creare una finestra di dialogo che consente agli utenti di selezionare gli elementi da un controllo casella di riepilogo.

## Creare un controllo casella di riepilogo e selezionare i relativi elementi
Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**. Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.

-   **Text.** Questo valore diventa il titolo della finestra.

-   **Size.** Le dimensioni del modulo, in pixel. Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.

-   **StartingPosition.** Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente. Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto. Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Creare quindi un pulsante **OK** per il modulo. Specificare le dimensioni e il comportamento del pulsante **OK**. In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro. L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel. Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Analogamente, creare un pulsante **Cancel**. Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare. In questo caso, si vuole che gli utenti selezionino un computer.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

Aggiungere il controllo, in questo caso una casella di riepilogo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta. Oltre alle caselle di riepilogo, è possibile applicare molti altri controlli. Per altri controlli, vedere [Spazio dei nomi System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) in MSDN.

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

Nella sezione seguente, specificare i valori che si vuole vengano visualizzati nella casella di riepilogo.

> [!NOTE]
> La casella di riepilogo creata da questo script consente di effettuare un'unica selezione. Per creare un controllo casella di riepilogo che consenta di eseguire selezioni multiple, specificare un valore per la proprietà **SelectionMode**, in modo simile al seguente:  `$listBox.SelectionMode = "MultiExtended"`. Per altre informazioni, vedere [Caselle di riepilogo a selezione multipla](Multiple-selection-List-Boxes.md).

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

Aggiungere il controllo casella di riepilogo nel modulo e indicare a Windows di aprire il modulo sopra altre finestre e finestre di dialogo.

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.

```
$result = $form.ShowDialog()
```

Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona un'opzione della casella di riepilogo e quindi fa clic su **OK** o preme **INVIO**.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## Vedere anche
[Hey, Scripting Guy! Blog - Weekend Scripter: Fixing PowerShell GUI Examples](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: dlwyatt/WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Windows PowerShell Tip of the Week](http://technet.microsoft.com/library/ff730949.aspx) (Windows PowerShell: suggerimento della settimana)



<!--HONumber=May16_HO2-->


