---
title: Risorsa PackageManagementSource DSC
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 22e61490e7b3f98335334a2703ec9639cbdaa87e
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
---
# <a name="dsc-packagemanagementsource-resource"></a>Risorsa PackageManagementSource DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione. **Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.** Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.

## <a name="syntax"></a>Sintassi

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| Nome| Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema.| 
| Ensure| Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione.| 
| InstallationPolicy| Determina se considerare attendibile l'origine del pacchetto. Uno dei valori possibili: "Untrusted", "Trusted".| 
| ProviderName| Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto.| 
| SourceUri| Specifica l'URI dell'origine del pacchetto.| 
| SourceCredential| Fornisce l'accesso al pacchetto in un'origine remota.| 

## <a name="example"></a>Esempio

Questo esempio registra l'origine del pacchetto http://nuget.org usando la risorsa DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```