---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: 09088c9e7307a26b86e82f2dc10d2648213c6bd2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseaddontoolcollection-object"></a>Oggetto ISEAddOnToolCollection
  L'oggetto **ISEAddOnToolCollection** è una raccolta di oggetti **ISEAddOnTool**. Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.

## <a name="methods"></a>Metodo

### <a name="add-name-controltype-isvisible-"></a>Add\( Name, ControlType, \[IsVisible\] \)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Aggiunge un nuovo strumento aggiuntivo alla raccolta. Restituisce lo strumento aggiuntivo appena aggiunto. Prima di eseguire questo comando, è necessario installare lo strumento aggiuntivo nel computer locale e caricare l'assembly.

 **Name**: la stringa specifica il nome visualizzato dello strumento aggiuntivo aggiunto a Windows PowerShell ISE.

 **ControlType**: il tipo specifica il controllo aggiunto.

 **\[IsVisible\]**: valore booleano facoltativo che se impostato su **$true** rende visibile lo strumento aggiuntivo nel riquadro associato degli strumenti.

```PowerShell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Rimuove lo strumento aggiuntivo specificato dalla raccolta.

 **Item**: Microsoft.PowerShell.Host.ISE.ISEAddOnTool specifica l'oggetto che deve essere rimosso da Windows PowerShell ISE.

```PowerShell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Seleziona la scheda di PowerShell specificata dal parametro **psTab**.

 **psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da selezionare.

```PowerShell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a>Remove\( psTab \)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Rimuove la scheda di PowerShell specificata dal parametro **psTab**.

 **psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da rimuovere.

```PowerShell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Vedere anche
- [Oggetto PowerShellTab](The-PowerShellTab-Object.md) 
- [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  