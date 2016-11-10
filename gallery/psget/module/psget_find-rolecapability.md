---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_find rolecapability
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: cdb675c32f62c5bd7acfb79357342f71960b50f4

---

# Find-RoleCapability

Consente di trovare funzionalità di ruolo nei moduli.

## Descrizione
Il cmdlet Find-RoleCapability consente di trovare funzionalità di ruolo PowerShell nei moduli. Find-RoleCapability cerca nei moduli dei repository registrati. Per ogni funzionalità di ruolo trovata, questo cmdlet restituisce un oggetto PSGetRoleCapabilityInfo. È possibile passare un oggetto PSGetRoleCapabilityInfo al cmdlet Install-Module per installare il modulo che contiene la funzionalità di ruolo.
Le funzionalità di ruolo PowerShell definiscono i comandi, le applicazioni e così via a disposizione dell'utente in un endpoint JEA (Just Enough Administration). Le funzionalità di ruolo vengono definite da file con estensione psrc.

- Find-RoleCapability consente di filtrare usando i parametri di versione MinimumVersion, RequiredVersion e AllVersions.
  - Questi parametri si escludono a vicenda.
  - Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.
  - Se il parametro RequiredVersion non è specificato, Find-RoleCapability restituisce la versione più recente del modulo maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo.
  - Se il parametro RequiredVersion è specificato, Find-RoleCapability restituisce unicamente la versione del modulo che corrisponde esattamente alla versione specificata.
- Find-RoleCapability consente di filtrare in base ai metadati del modulo usando il parametro -Tag
- Find-RoleCapability consente di filtrare in base al linguaggio di ricerca specifico del repository usando il parametro -Filter.
- Find-RoleCapability consente di filtrare in base ai moduli di tutti o alcuni dei repository registrati.

## Sintassi del cmdlet
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## Riferimento per la Guida online sui cmdlet

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## Comandi di esempio
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```




<!--HONumber=Oct16_HO2-->

