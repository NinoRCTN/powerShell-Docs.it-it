---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="new-temporaryfile" class="xliff"></a>
# New-TemporaryFile
A volte, negli script è necessario creare un file temporaneo. È possibile farlo facilmente con il cmdlet **New-TemporaryFile**:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp

