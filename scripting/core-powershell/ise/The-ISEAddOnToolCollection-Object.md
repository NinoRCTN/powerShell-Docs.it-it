---
title:  Oggetto ISEAddOnToolCollection
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  634eab89-0845-4016-974b-361b09bb8f7b
---

# Oggetto ISEAddOnToolCollection
  L'oggetto **ISEAddOnToolCollection** è una raccolta di oggetti **ISEAddOnTool**. Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.

## Metodo

### Add( Name, ControlType, [IsVisible] )
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Aggiunge un nuovo strumento aggiuntivo alla raccolta. Restituisce lo strumento aggiuntivo appena aggiunto. Prima di eseguire questo comando, è necessario installare lo strumento aggiuntivo nel computer locale e caricare l'assembly.

 **Name**: stringa  Specifica il nome visualizzato dello strumento aggiuntivo che viene aggiunto a Windows PowerShell ISE.

 **ControlType**: tipo  Specifica il controllo aggiunto.

 **\[IsVisible\]** (facoltativo): booleano  Se impostato su **$true**, lo strumento aggiuntivo è immediatamente visibile nel riquadro degli strumenti associato.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### Remove( Item )
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Rimuove lo strumento aggiuntivo specificato dalla raccolta.

 **Item**: Microsoft.PowerShell.Host.ISE.ISEAddOnTool  Specifica l'oggetto da rimuovere da Windows PowerShell ISE.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### SetSelectedPowerShellTab( psTab )
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Seleziona la scheda di PowerShell specificata dal parametro **psTab**.

 **psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab  Scheda di PowerShell da selezionare.

```

      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"

```

### Remove( psTab )
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Rimuove la scheda di PowerShell specificata dal parametro **psTab**.

 **psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab  Scheda di PowerShell da rimuovere.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## Vedere anche
 [Oggetto PowerShellTab](The-PowerShellTab-Object.md) 
 [The Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) (Modello a oggetti di scripting di Windows PowerShell ISE) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


