---
title: Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064714"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="12523-102">Elemento ScriptBlock per ItemSelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="12523-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="12523-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="12523-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="12523-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="12523-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="12523-105">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="12523-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="12523-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition ExpressionBinding per i controlli elemento di visualizzazione (formato) ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="12523-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12523-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="12523-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12523-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="12523-108">Attributes and Elements</span></span>

<span data-ttu-id="12523-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="12523-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12523-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="12523-110">Attributes</span></span>

<span data-ttu-id="12523-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="12523-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12523-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="12523-112">Child Elements</span></span>

<span data-ttu-id="12523-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="12523-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12523-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="12523-114">Parent Elements</span></span>

|<span data-ttu-id="12523-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="12523-115">Element</span></span>|<span data-ttu-id="12523-116">Description</span><span class="sxs-lookup"><span data-stu-id="12523-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12523-117">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="12523-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="12523-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="12523-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="12523-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="12523-119">Text Value</span></span>

<span data-ttu-id="12523-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="12523-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="12523-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="12523-121">Remarks</span></span>

<span data-ttu-id="12523-122">Se questo elemento viene usato, è possibile specificare il [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="12523-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="12523-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12523-123">See Also</span></span>

[<span data-ttu-id="12523-124">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="12523-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="12523-125">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="12523-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="12523-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="12523-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
