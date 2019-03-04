---
title: Elemento larghezza per TableColumnHeader per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853107"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Width per TableColumnHeader per TableControl (formato)

Definisce la larghezza (in caratteri) di una colonna.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento di configurazione per Table (formato) TableHeaders TableColumnHeader elemento per elemento larghezza Table (formato) TableColumnHeader per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Width` elemento utilizzato quando si definiscono le intestazioni di colonna.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader per TableHeaders per TbleControl (formato)](./tablecolumnheader-element-format.md)|Definisce un'etichetta, larghezza e l'allineamento dei dati per una colonna della tabella.|

## <a name="text-value"></a>Valore di testo

Quando si trova in tutte le possibili, specificare una larghezza (in caratteri) che è maggiore della lunghezza dei valori di proprietà visualizzata.

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra un `TableColumnHeader` elemento la cui larghezza è 16 caratteri.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader per TableHeader per Table (formato)](./tablecolumnheader-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)