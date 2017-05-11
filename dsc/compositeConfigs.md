---
title: Annidamento delle configurazioni
ms.date: 2017-03-27
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: carmonm
ms.prod: powershell
ms.openlocfilehash: 3afc4c87b1bc54e5f251a3a54eab5f448900f124
ms.sourcegitcommit: 65250232157bb1c742d7d385933b8abc24a570fb
translationtype: HT
---
# <a name="nesting-dsc-configurations"></a>Annidamento delle configurazioni DSC

Una configurazione annidata (denominata anche configurazione composita) è una configurazione che viene chiamata all'interno di un'altra configurazione come se fosse una risorsa.
Entrambe le configurazioni devono essere definite nello stesso file.

Ecco un esempio semplice:

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

In questo esempio, `FileConfig` accetta due parametri obbligatori, **CopyFrom** e **CopyTo**, che vengono usati come valori per le proprietà **SourcePath** e **DestinationPath** nel blocco di risorse `File`. La configurazione `NestedConfig` chiama `FileConfig` come se fosse una risorsa.
Le proprietà nel blocco di risorse `NestedConfig` (**CopyFrom** e **CopyTo**) sono i parametri della configurazione `FileConfig`.

## <a name="see-also"></a>Vedere anche

- [Risorse composite: uso di una configurazione DSC come risorsa](authoringResourceComposite.md)