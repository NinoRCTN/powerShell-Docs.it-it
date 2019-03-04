---
title: Elemento ScriptBlock per WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858027"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="7ebf7-102">Elemento ScriptBlock per WideItem per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7ebf7-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="7ebf7-103">Specifica lo script il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="7ebf7-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) elemento WideItem (formato) ScriptBlock elemento di configurazione per WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7ebf7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ebf7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7ebf7-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ebf7-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7ebf7-106">Attributes and Elements</span></span>

<span data-ttu-id="7ebf7-107">Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ebf7-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7ebf7-108">Attributes</span></span>

<span data-ttu-id="7ebf7-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ebf7-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7ebf7-110">Child Elements</span></span>

<span data-ttu-id="7ebf7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7ebf7-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7ebf7-112">Parent Elements</span></span>

|<span data-ttu-id="7ebf7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7ebf7-113">Element</span></span>|<span data-ttu-id="7ebf7-114">Description</span><span class="sxs-lookup"><span data-stu-id="7ebf7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ebf7-115">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7ebf7-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="7ebf7-116">Definisce il blocco di script o proprietà il cui valore viene visualizzato in visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7ebf7-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="7ebf7-117">Text Value</span></span>

<span data-ttu-id="7ebf7-118">Specificare lo script il cui valore viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ebf7-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7ebf7-119">Remarks</span></span>

<span data-ttu-id="7ebf7-120">Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7ebf7-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7ebf7-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="7ebf7-121">Example</span></span>

<span data-ttu-id="7ebf7-122">Questo esempio viene illustrato un `WideItem` elemento che definisce uno script il cui valore viene visualizzato nella vista.</span><span class="sxs-lookup"><span data-stu-id="7ebf7-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="7ebf7-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7ebf7-123">See Also</span></span>

[<span data-ttu-id="7ebf7-124">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7ebf7-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="7ebf7-125">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7ebf7-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7ebf7-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ebf7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
