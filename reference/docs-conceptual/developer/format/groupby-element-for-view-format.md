---
title: Elemento GroupBy per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363630"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="ebc1a-102">Elemento GroupBy per View (formato)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="ebc1a-103">Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="ebc1a-104">Questo elemento viene utilizzato quando si definisce una tabella, un elenco, un'ampia o una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="ebc1a-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ebc1a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ebc1a-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ebc1a-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ebc1a-107">Attributes and Elements</span></span>

<span data-ttu-id="ebc1a-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebc1a-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="ebc1a-109">Attributes</span></span>

<span data-ttu-id="ebc1a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ebc1a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ebc1a-111">Child Elements</span></span>

|<span data-ttu-id="ebc1a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ebc1a-112">Element</span></span>|<span data-ttu-id="ebc1a-113">Description</span><span class="sxs-lookup"><span data-stu-id="ebc1a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebc1a-114">Elemento CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="ebc1a-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ebc1a-116">Definisce il controllo personalizzato che Visualizza i nuovi gruppi.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="ebc1a-117">Elemento CustomControlName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="ebc1a-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ebc1a-119">Specifica il nome di un controllo utilizzato per visualizzare il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="ebc1a-120">Elemento label per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="ebc1a-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ebc1a-122">Specifica un'etichetta visualizzata quando viene rilevato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="ebc1a-123">Elemento PropertyName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="ebc1a-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ebc1a-125">Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che cambia il valore.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="ebc1a-126">Elemento ScriptBlock per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="ebc1a-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-127">Optional element.</span></span><br /><br /> <span data-ttu-id="ebc1a-128">Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il valore.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ebc1a-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ebc1a-129">Parent Elements</span></span>

|<span data-ttu-id="ebc1a-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="ebc1a-130">Element</span></span>|<span data-ttu-id="ebc1a-131">Description</span><span class="sxs-lookup"><span data-stu-id="ebc1a-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebc1a-132">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ebc1a-133">Definisce una vista che visualizza uno o più oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ebc1a-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ebc1a-134">Remarks</span></span>

<span data-ttu-id="ebc1a-135">Quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti, è necessario specificare la proprietà o lo script che avvierà il nuovo gruppo. Tuttavia, non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebc1a-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ebc1a-136">See Also</span></span>

[<span data-ttu-id="ebc1a-137">Elemento CustomControlName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="ebc1a-138">Elemento label per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="ebc1a-139">Elemento PropertyName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="ebc1a-140">Elemento ScriptBlock per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="ebc1a-141">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="ebc1a-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ebc1a-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebc1a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)