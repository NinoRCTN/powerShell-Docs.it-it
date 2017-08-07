---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Gerarchia del modello a oggetti ISE
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: 0d0370ed9f64464038e643ae2cd241891fa74f33
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="7ab30-103">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="7ab30-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="7ab30-104">Questo argomento illustra la gerarchia di oggetti che fanno parte di Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="7ab30-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="7ab30-105">Windows PowerShell ISE è incluso in Windows PowerShell 3.0 e in Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="7ab30-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="7ab30-106">Fare clic su un oggetto per accedere alla documentazione di riferimento per la classe che definisce l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="7ab30-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <span data-ttu-id="7ab30-107"><a name="psISE"></a> **Oggetto $psISE**</span><span class="sxs-lookup"><span data-stu-id="7ab30-107"><a name="psISE"></a> **$psISE Object**</span></span>
 <span data-ttu-id="7ab30-108">L'oggetto **$psISE** è l'[oggetto radice](The-ObjectModelRoot-Object.md) della gerarchia di oggetti di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ab30-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="7ab30-109">Si trova al livello superiore, rendendo disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="7ab30-110">**[$psISE.CurrentFile](#currentfile)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-110">**[$psISE.CurrentFile](#currentfile)**</span></span>

-   <span data-ttu-id="7ab30-111">**[$psISE.CurrentPowerShellTab](#currentpowershelltab)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-111">**[$psISE.CurrentPowerShellTab](#currentpowershelltab)**</span></span>

-   <span data-ttu-id="7ab30-112">**[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-112">**[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**</span></span>

-   <span data-ttu-id="7ab30-113">**[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-113">**[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**</span></span>

-   <span data-ttu-id="7ab30-114">**[$psISE.Options](#options)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-114">**[$psISE.Options](#options)**</span></span>

-   <span data-ttu-id="7ab30-115">**[$psISE.PowerShellTabs](#powershelltabs)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-115">**[$psISE.PowerShellTabs](#powershelltabs)**</span></span>

##  <span data-ttu-id="7ab30-116"><a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-116"><a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="7ab30-117">L'oggetto **$psISE.CurrentFile** è un'istanza della classe [ISEFile](The-ISEFile-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="7ab30-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**</span></span>

-   <span data-ttu-id="7ab30-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**: questo oggetto è un'istanza della classe [ISEEditor](The-ISEEditor-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="7ab30-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span></span>

    -   <span data-ttu-id="7ab30-121">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-121">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span></span>

    -   <span data-ttu-id="7ab30-122">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-122">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span></span>

    -   <span data-ttu-id="7ab30-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span></span>

    -   <span data-ttu-id="7ab30-124">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-124">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span></span>

    -   <span data-ttu-id="7ab30-125">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-125">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span></span>

    -   <span data-ttu-id="7ab30-126">**[Text](The-ISEEditor-Object.md#Text)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-126">**[Text](The-ISEEditor-Object.md#Text)**</span></span>

-   <span data-ttu-id="7ab30-127">**[Encoding](The-ISEFile-Object.md#Encoding)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-127">**[Encoding](The-ISEFile-Object.md#Encoding)**</span></span>

-   <span data-ttu-id="7ab30-128">**[FullPath](The-ISEFile-Object.md#FullPath)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-128">**[FullPath](The-ISEFile-Object.md#FullPath)**</span></span>

-   <span data-ttu-id="7ab30-129">**[IsSaved](The-ISEFile-Object.md#IsSaved)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-129">**[IsSaved](The-ISEFile-Object.md#IsSaved)**</span></span>

-   <span data-ttu-id="7ab30-130">**[IsUntitled](The-ISEFile-Object.md#IsUntitled)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-130">**[IsUntitled](The-ISEFile-Object.md#IsUntitled)**</span></span>

##  <span data-ttu-id="7ab30-131"><a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-131"><a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="7ab30-132">L'oggetto **$psISE.CurrentPowerShellTab** è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="7ab30-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**: questo oggetto è un'istanza della classe [ISEMenuItem](The-ISEMenuItem-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="7ab30-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**</span></span>

    -   <span data-ttu-id="7ab30-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**</span></span>

    -   <span data-ttu-id="7ab30-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**</span></span>

    -   <span data-ttu-id="7ab30-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-138">**[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-138">**[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**</span></span>

-   <span data-ttu-id="7ab30-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**: questo oggetto è un'istanza della classe [ISEEditor](The-ISEEditor-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="7ab30-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span></span>

    -   <span data-ttu-id="7ab30-141">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-141">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span></span>

    -   <span data-ttu-id="7ab30-142">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-142">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span></span>

    -   <span data-ttu-id="7ab30-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span></span>

    -   <span data-ttu-id="7ab30-144">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-144">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span></span>

    -   <span data-ttu-id="7ab30-145">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-145">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span></span>

    -   <span data-ttu-id="7ab30-146">**[Text](The-ISEEditor-Object.md#Text)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-146">**[Text](The-ISEEditor-Object.md#Text)**</span></span>

-   <span data-ttu-id="7ab30-147">**[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-147">**[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**</span></span>

-   <span data-ttu-id="7ab30-148">**[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-148">**[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**</span></span>

-   <span data-ttu-id="7ab30-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**</span></span>

-   <span data-ttu-id="7ab30-152">**[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-152">**[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**</span></span>

-   <span data-ttu-id="7ab30-153">**[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-153">**[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**</span></span>

-   <span data-ttu-id="7ab30-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-155">**[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-155">**[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**</span></span>

-   <span data-ttu-id="7ab30-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**</span></span>

-   <span data-ttu-id="7ab30-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <span data-ttu-id="7ab30-160"><a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="7ab30-160"><a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="7ab30-161">L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="7ab30-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="7ab30-162">Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo superiore della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ab30-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="7ab30-163">Questo oggetto rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="7ab30-164">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-164">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span></span>

-   <span data-ttu-id="7ab30-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span></span>

-   <span data-ttu-id="7ab30-166">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-166">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span></span>

##  <span data-ttu-id="7ab30-167"><a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="7ab30-167"><a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="7ab30-168">L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="7ab30-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="7ab30-169">Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo destro della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ab30-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="7ab30-170">Questo oggetto rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="7ab30-171">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-171">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span></span>

-   <span data-ttu-id="7ab30-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span></span>

-   <span data-ttu-id="7ab30-173">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-173">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span></span>

##  <span data-ttu-id="7ab30-174"><a name="Options"></a> **$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="7ab30-174"><a name="Options"></a> **$psISE.Options**</span></span>
 <span data-ttu-id="7ab30-175">L'oggetto **$psISE.Options** rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="7ab30-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="7ab30-176">**[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-176">**[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**</span></span>

-   <span data-ttu-id="7ab30-177">**[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-177">**[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**</span></span>

-   <span data-ttu-id="7ab30-178">**[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-178">**[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**</span></span>

-   <span data-ttu-id="7ab30-179">**[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-179">**[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**</span></span>

-   <span data-ttu-id="7ab30-180">**[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-180">**[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**</span></span>

-   <span data-ttu-id="7ab30-181">**[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-181">**[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**</span></span>

-   <span data-ttu-id="7ab30-182">**[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-182">**[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**</span></span>

-   <span data-ttu-id="7ab30-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="7ab30-184">**[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-184">**[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**</span></span>

-   <span data-ttu-id="7ab30-185">**[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-185">**[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**</span></span>

-   <span data-ttu-id="7ab30-186">**[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-186">**[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**</span></span>

-   <span data-ttu-id="7ab30-187">**[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-187">**[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**</span></span>

-   <span data-ttu-id="7ab30-188">**[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-188">**[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**</span></span>

-   <span data-ttu-id="7ab30-189">**[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-189">**[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**</span></span>

-   <span data-ttu-id="7ab30-190">**[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-190">**[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**</span></span>

-   <span data-ttu-id="7ab30-191">**[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-191">**[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**</span></span>

-   <span data-ttu-id="7ab30-192">**[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-192">**[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**</span></span>

-   <span data-ttu-id="7ab30-193">**[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-193">**[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**</span></span>

-   <span data-ttu-id="7ab30-194">**[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-194">**[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**</span></span>

-   <span data-ttu-id="7ab30-195">**[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-195">**[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**</span></span>

-   <span data-ttu-id="7ab30-196">**[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-196">**[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**</span></span>

-   <span data-ttu-id="7ab30-197">**[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-197">**[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**</span></span>

-   <span data-ttu-id="7ab30-198">**[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-198">**[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**</span></span>

-   <span data-ttu-id="7ab30-199">**[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-199">**[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**</span></span>

-   <span data-ttu-id="7ab30-200">**[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-200">**[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**</span></span>

-   <span data-ttu-id="7ab30-201">**[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-201">**[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**</span></span>

-   <span data-ttu-id="7ab30-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**</span></span>

-   <span data-ttu-id="7ab30-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**</span></span>

-   <span data-ttu-id="7ab30-204">**[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-204">**[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**</span></span>

-   <span data-ttu-id="7ab30-205">**[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-205">**[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**</span></span>

-   <span data-ttu-id="7ab30-206">**[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-206">**[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**</span></span>

-   <span data-ttu-id="7ab30-207">**[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-207">**[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**</span></span>

-   <span data-ttu-id="7ab30-208">**[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-208">**[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**</span></span>

-   <span data-ttu-id="7ab30-209">**[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-209">**[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**</span></span>

-   <span data-ttu-id="7ab30-210">**[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-210">**[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**</span></span>

##  <span data-ttu-id="7ab30-211"><a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="7ab30-211"><a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="7ab30-212">L'oggetto **$psISE.PowerShellTabs** è un'istanza della classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="7ab30-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="7ab30-213">È una raccolta di tutte le schede di PowerShell attualmente aperte che rappresentano gli ambienti di esecuzione di Windows PowerShell disponibili nel computer locale o nei computer remoti connessi.</span><span class="sxs-lookup"><span data-stu-id="7ab30-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="7ab30-214">Ogni membro della raccolta è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="7ab30-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ab30-215">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7ab30-215">See Also</span></span>
- [<span data-ttu-id="7ab30-216">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7ab30-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7ab30-217">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7ab30-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

