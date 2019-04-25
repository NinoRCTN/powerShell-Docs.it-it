---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085882"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="3286b-102">Chiamare il costruttore della classe di base</span><span class="sxs-lookup"><span data-stu-id="3286b-102">Call Base Class Constructor</span></span>

<span data-ttu-id="3286b-103">Per chiamare un costruttore di classe di base da una sottoclasse, usare la parola chiave **base**:</span><span class="sxs-lookup"><span data-stu-id="3286b-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="3286b-104">Se una classe di base ha un costruttore predefinito (nessun parametro), è possibile omettere una chiamata esplicita al costruttore:</span><span class="sxs-lookup"><span data-stu-id="3286b-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
