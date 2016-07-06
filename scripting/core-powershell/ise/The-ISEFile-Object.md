---
title: Oggetto ISEFile
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: ce9364e8fb73a2d31b728430c590fef4175ebe26

---

# Oggetto ISEFile
  Un oggetto **ISEFile** rappresenta un file in Windows PowerShell® Integrated Scripting Environment (ISE). È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEFile. Questo argomento elenca i relativi metodi membro e le proprietà del membro. L'oggetto **$psISE.CurrentFile** e i file nella raccolta File in una scheda di PowerShell sono tutte istanze della classe Microsoft.PowerShell.Host.ISE.ISEFile.

## Metodo

###  <a name="save-override"></a> Save\( \[saveEncoding\] \)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Salva il file su disco.

 **\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 facoltativo Parametro di codifica caratteri facoltativo da usare per il file salvato. Il valore predefinito è **UTF8**.

 **Eccezioni**
 -   **System.IO.IOException**: non è stato possibile salvare il file.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Salva il file con il nome file e la codifica specificati.

 **filename** \- Stringa Nome da usare per salvare il file.

 **\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 facoltativo Parametro di codifica caratteri facoltativo da usare per il file salvato. Il valore predefinito è **UTF8**.

 **Eccezioni**
 -   **System.ArgumentNullException**: il parametro **filename** è Null.

-   **System.ArgumentException**: il parametro **filename** è vuoto.

-   **System.IO.IOException**: non è stato possibile salvare il file.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## Proprietà

###  <a name="Displayname"></a> DisplayName
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene la stringa contenente il nome visualizzato di questo file. Il nome viene visualizzato nella scheda **File** nella parte superiore dell'editor. La presenza di un asterisco (\(\*\)) alla fine del nome indica che il file contiene modifiche che non sono state salvate.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <a name="Editor"></a> Editor
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene [l'oggetto editor](The-ISEEditor-Object.md) usato per il file specificato.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <a name="Encoding"></a> Encoding
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene la codifica del file originale. Si tratta di un oggetto **System.Text.Encoding**.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <a name="FullPath"></a> FullPath
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene la stringa che specifica il percorso completo del file aperto.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <a name="IsSaved"></a> IsSaved
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà booleana di sola lettura che restituisce **$true** se il file è stato salvato dopo l'ultima modifica.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <a name="IsUntitled"></a> IsUntitled
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che restituisce **$true** se al file non è mai stato assegnato un titolo.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## Vedere anche
 [Oggetto ISEFileCollection](The-ISEFileCollection-Object.md) 
 [Modello a oggetti di Scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Jun16_HO4-->


