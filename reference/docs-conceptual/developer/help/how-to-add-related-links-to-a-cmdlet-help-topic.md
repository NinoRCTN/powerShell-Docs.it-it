---
title: Come aggiungere collegamenti correlati a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361220"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="5f182-102">Come aggiungere collegamenti correlati a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f182-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="5f182-103">Questa sezione descrive come aggiungere riferimenti ad altri contenuti correlati a un argomento della guida del cmdlet di® di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f182-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="5f182-104">Poiché questi riferimenti vengono visualizzati in una finestra di comando, non si collegano direttamente al contenuto a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="5f182-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="5f182-105">Negli argomenti della guida sui cmdlet inclusi in Windows PowerShell®, questi collegamenti fanno riferimento ad altri cmdlet, al contenuto concettuale ("about_") e ad altri documenti e file della guida non correlati ai® di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f182-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="5f182-106">Nel codice XML seguente viene illustrato come aggiungere un nodo RelatedLinks contenente due riferimenti ad argomenti correlati.</span><span class="sxs-lookup"><span data-stu-id="5f182-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



