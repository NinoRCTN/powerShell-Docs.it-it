---
title: Elemento PropertyName per ItemSelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362410"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="4cb4f-102">Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4cb4f-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="4cb4f-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4cb4f-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="4cb4f-105">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4cb4f-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento CustomItem di GroupBy (Format) per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) ItemSelectionCondition per Expression per l'elemento GroupBy (Format) PropertyName per ItemSelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cb4f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4cb4f-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4cb4f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4cb4f-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4cb4f-108">Attributes and Elements</span></span>

<span data-ttu-id="4cb4f-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4cb4f-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="4cb4f-110">Attributes</span></span>

<span data-ttu-id="4cb4f-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4cb4f-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4cb4f-112">Child Elements</span></span>

<span data-ttu-id="4cb4f-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4cb4f-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4cb4f-114">Parent Elements</span></span>

|<span data-ttu-id="4cb4f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4cb4f-115">Element</span></span>|<span data-ttu-id="4cb4f-116">Description</span><span class="sxs-lookup"><span data-stu-id="4cb4f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4cb4f-117">Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cb4f-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="4cb4f-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4cb4f-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="4cb4f-119">Text Value</span></span>

<span data-ttu-id="4cb4f-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="4cb4f-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4cb4f-121">Remarks</span></span>

<span data-ttu-id="4cb4f-122">Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="4cb4f-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cb4f-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4cb4f-123">See Also</span></span>

[<span data-ttu-id="4cb4f-124">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cb4f-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="4cb4f-125">Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cb4f-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4cb4f-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cb4f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
