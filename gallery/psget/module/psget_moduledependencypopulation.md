---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_moduledependencypopulation
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: a6ace8faebd6f37d3c41ee5a3fef2bda70b8c651

---

# Logica per la preparazione di dipendenze dei moduli durante l'operazione di pubblicazione
1.  I moduli elencati in RequiredModules vengono considerati dipendenze.
2.  I moduli elencati in NestedModules e la cui base del modulo non è inclusa nella base del modulo specificata vengono considerati dipendenze.

3.  Le dipendenze precedenti devono essere disponibili nello stesso repository di destinazione. In caso contrario l'operazione di pubblicazione ha esito negativo.
    Ad esempio: se 'SnippetPx' non è disponibile nel repository, viene generato l'errore seguente.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Alcune dipendenze del modulo possono essere gestite esternamente. In tal caso devono essere aggiunte alla voce ExternalModuleDependencies nella sezione PSData del manifesto del modulo.
    Di seguito è riportata una parte del messaggio di errore precedente:
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Durante l'installazione del modulo, l'elenco di dipendenze preparato in precedenza viene usato per installare le dipendenze.*

*Verificare la disponibilità delle dipendenze del modulo in $env:PSModulePath nel sistema durante l'operazione di pubblicazione.*




<!--HONumber=Oct16_HO2-->

