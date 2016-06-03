---
title:  Riferimenti al modello a oggetti di Windows PowerShell ISE
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
---

# Riferimenti al modello a oggetti di Windows PowerShell ISE
  
## Riferimento del modello a oggetti
 Questa sezione fornisce un riferimento per le classi sottostanti che definiscono i vari oggetti in Windows PowerShell® Integrated Scripting Environment (ISE). Per visualizzare gli oggetti organizzati nella relativa gerarchia, vedere [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md).

 [Oggetto ISEAddOnTool](The-ISEAddOnTool-Object.md)
 Esempi: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [Oggetto ISEAddOnTool](The-ISEAddOnTool-Object.md)
  [Oggetto ISEEditor](The-ISEEditor-Object.md)
 Esempi: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [Oggetto ISEFile](The-ISEFile-Object.md)
 Esempi: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [Oggetto ISEFileCollection](The-ISEFileCollection-Object.md)
 Esempi: $psISE.PowerShellTabs.Files.

 [Oggetto ISEMenuItem](The-ISEMenuItem-Object.md)
 Esempi: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [Oggetto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
 Esempio: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [Oggetto ISEOptions](The-ISEOptions-Object.md)
 Esempi: $psISE.Options, $psISE.Options.DefaultOptions.

 [Oggetto ObjectModelRoot](The-ObjectModelRoot-Object.md)
 Esempio: oggetto $psISE radice.

 [Oggetto PowerShellTab](The-PowerShellTab-Object.md)
 Esempi: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [Oggetto PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
 Esempio: $psISE.PowerShellTabs.

## Vedere anche
 [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


