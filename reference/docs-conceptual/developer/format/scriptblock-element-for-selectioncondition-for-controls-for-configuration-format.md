---
title: Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368620"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="c32bc-102">Elemento ScriptBlock per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="c32bc-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c32bc-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c32bc-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c32bc-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="c32bc-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="c32bc-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c32bc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c32bc-106">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per i controlli per la configurazione (Format) Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c32bc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c32bc-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c32bc-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c32bc-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c32bc-108">Attributes and Elements</span></span>

<span data-ttu-id="c32bc-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="c32bc-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c32bc-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="c32bc-110">Attributes</span></span>

<span data-ttu-id="c32bc-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c32bc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c32bc-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c32bc-112">Child Elements</span></span>

<span data-ttu-id="c32bc-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c32bc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c32bc-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c32bc-114">Parent Elements</span></span>

|<span data-ttu-id="c32bc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c32bc-115">Element</span></span>|<span data-ttu-id="c32bc-116">Description</span><span class="sxs-lookup"><span data-stu-id="c32bc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c32bc-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c32bc-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="c32bc-118">Definisce una condizione che deve esistere per la definizione del controllo comune da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="c32bc-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c32bc-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c32bc-119">Text Value</span></span>

<span data-ttu-id="c32bc-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="c32bc-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c32bc-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c32bc-121">Remarks</span></span>

<span data-ttu-id="c32bc-122">Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="c32bc-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="c32bc-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c32bc-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c32bc-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c32bc-124">See Also</span></span>

[<span data-ttu-id="c32bc-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c32bc-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="c32bc-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c32bc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)