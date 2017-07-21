---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="ae389-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="ae389-103">Find-RoleCapability</span></span>

<span data-ttu-id="ae389-104">Consente di trovare funzionalità di ruolo nei moduli.</span><span class="sxs-lookup"><span data-stu-id="ae389-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="ae389-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ae389-105">Description</span></span>
<span data-ttu-id="ae389-106">Il cmdlet Find-RoleCapability consente di trovare funzionalità di ruolo PowerShell nei moduli.</span><span class="sxs-lookup"><span data-stu-id="ae389-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="ae389-107">Find-RoleCapability cerca nei moduli dei repository registrati.</span><span class="sxs-lookup"><span data-stu-id="ae389-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="ae389-108">Per ogni funzionalità di ruolo trovata, questo cmdlet restituisce un oggetto PSGetRoleCapabilityInfo.</span><span class="sxs-lookup"><span data-stu-id="ae389-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="ae389-109">È possibile passare un oggetto PSGetRoleCapabilityInfo al cmdlet Install-Module per installare il modulo che contiene la funzionalità di ruolo.</span><span class="sxs-lookup"><span data-stu-id="ae389-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="ae389-110">Le funzionalità di ruolo PowerShell definiscono i comandi, le applicazioni e così via a disposizione dell'utente in un endpoint JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="ae389-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="ae389-111">Le funzionalità di ruolo vengono definite da file con estensione psrc.</span><span class="sxs-lookup"><span data-stu-id="ae389-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="ae389-112">Find-RoleCapability consente di filtrare usando i parametri di versione MinimumVersion, RequiredVersion e AllVersions.</span><span class="sxs-lookup"><span data-stu-id="ae389-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="ae389-113">Questi parametri si escludono a vicenda.</span><span class="sxs-lookup"><span data-stu-id="ae389-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="ae389-114">Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="ae389-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="ae389-115">Se il parametro RequiredVersion non è specificato, Find-RoleCapability restituisce la versione più recente del modulo maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo.</span><span class="sxs-lookup"><span data-stu-id="ae389-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="ae389-116">Se il parametro RequiredVersion è specificato, Find-RoleCapability restituisce unicamente la versione del modulo che corrisponde esattamente alla versione specificata.</span><span class="sxs-lookup"><span data-stu-id="ae389-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="ae389-117">Find-RoleCapability consente di filtrare in base ai metadati del modulo usando il parametro -Tag</span><span class="sxs-lookup"><span data-stu-id="ae389-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="ae389-118">Find-RoleCapability consente di filtrare in base al linguaggio di ricerca specifico del repository usando il parametro -Filter.</span><span class="sxs-lookup"><span data-stu-id="ae389-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="ae389-119">Find-RoleCapability consente di filtrare in base ai moduli di tutti o alcuni dei repository registrati.</span><span class="sxs-lookup"><span data-stu-id="ae389-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ae389-120">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae389-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ae389-121">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae389-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="ae389-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="ae389-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="ae389-123">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="ae389-123">Example commands</span></span>
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

