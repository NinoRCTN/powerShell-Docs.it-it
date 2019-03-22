---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Uso di DSC in Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054663"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="1a95b-103">Uso di DSC in Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a95b-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="1a95b-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1a95b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1a95b-105">**DSC on Nano Server** (DSC su Nano Server) è un pacchetto opzionale contenuto nella cartella `NanoServer\Packages` del supporto Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="1a95b-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="1a95b-106">Il pacchetto può essere installato durante la creazione di un disco rigido virtuale per un Nano Server, specificando **Microsoft-NanoServer-DSC-Package** come valore del parametro **Packages** della funzione**New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="1a95b-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="1a95b-107">Se ad esempio si sta creando un disco rigido virtuale per una macchina virtuale, il comando potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="1a95b-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="1a95b-108">Per informazioni sull'installazione e l'uso di Nano Server e su come gestire Nano Server con la comunicazione remota di PowerShell, vedere [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Guida introduttiva a Nano Server).</span><span class="sxs-lookup"><span data-stu-id="1a95b-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="1a95b-109">Funzionalità DSC disponibili su Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a95b-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="1a95b-110">Poiché Nano Server supporta solo un set limitato di API rispetto a una versione completa di Windows Server, al momento DSC on Nano Server (DSC su Nano Server) non offre parità funzionale completa con DSC in esecuzione su SKU completi.</span><span class="sxs-lookup"><span data-stu-id="1a95b-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="1a95b-111">DSC on Nano Server (DSC su Nano Server) è in fase di sviluppo attivo e non è ancora completo di tutte le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="1a95b-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="1a95b-112">Le funzionalità DSC seguenti sono attualmente disponibili in Nano Server:</span><span class="sxs-lookup"><span data-stu-id="1a95b-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="1a95b-113">Modalità push e pull</span><span class="sxs-lookup"><span data-stu-id="1a95b-113">Both push and pull modes</span></span>

- <span data-ttu-id="1a95b-114">Tutti i cmdlet DSC presenti in una versione completa di Windows Server, inclusi i seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a95b-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="1a95b-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1a95b-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="1a95b-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1a95b-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="1a95b-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="1a95b-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="1a95b-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="1a95b-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="1a95b-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="1a95b-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="1a95b-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="1a95b-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="1a95b-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="1a95b-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="1a95b-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1a95b-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="1a95b-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="1a95b-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="1a95b-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="1a95b-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="1a95b-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="1a95b-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="1a95b-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="1a95b-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="1a95b-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="1a95b-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="1a95b-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="1a95b-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="1a95b-132">Compilazione di configurazioni. Vedere [Configurazioni DSC](../configurations/configurations.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="1a95b-133">**Problema:** la crittografia delle password durante la compilazione della configurazione non funziona. Vedere [Protezione del file MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="1a95b-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="1a95b-134">Compilazione di metaconfigurazioni. Vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="1a95b-135">Esecuzione di una risorsa nel contesto utente. Vedere [Esecuzione di DSC con le credenziali dell'utente](../configurations/runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="1a95b-136">Risorse basate su classi. Vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](../resources/authoringResourceClass.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="1a95b-137">Debug di risorse DSC. Vedere [Debug di risorse DSC](../troubleshooting/debugResource.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="1a95b-138">**Problema:** non funziona se una risorsa usa PsDscRunAsCredential. Vedere [Esecuzione di DSC con le credenziali dell'utente](../configurations/runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="1a95b-139">Specifica delle dipendenze tra nodi</span><span class="sxs-lookup"><span data-stu-id="1a95b-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="1a95b-140">Controllo delle versioni delle risorse</span><span class="sxs-lookup"><span data-stu-id="1a95b-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="1a95b-141">Client di pull, configurazione e risorse. Vedere [Configurazione di un client di pull usando nomi di configurazione](../pull-server/pullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="1a95b-142">Configurazioni parziali (pull e push)</span><span class="sxs-lookup"><span data-stu-id="1a95b-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="1a95b-143">Segnalazione a un server di pull</span><span class="sxs-lookup"><span data-stu-id="1a95b-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="1a95b-144">Crittografia MOF</span><span class="sxs-lookup"><span data-stu-id="1a95b-144">MOF encryption</span></span>

- <span data-ttu-id="1a95b-145">Registrazione degli eventi</span><span class="sxs-lookup"><span data-stu-id="1a95b-145">Event logging</span></span>

- <span data-ttu-id="1a95b-146">Creazione di report DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="1a95b-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="1a95b-147">Risorse completamente funzionanti</span><span class="sxs-lookup"><span data-stu-id="1a95b-147">Resources that are fully functional</span></span>

- <span data-ttu-id="1a95b-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="1a95b-148">**Archive**</span></span>
- <span data-ttu-id="1a95b-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="1a95b-149">**Environment**</span></span>
- <span data-ttu-id="1a95b-150">**File**</span><span class="sxs-lookup"><span data-stu-id="1a95b-150">**File**</span></span>
- <span data-ttu-id="1a95b-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="1a95b-151">**Log**</span></span>
- <span data-ttu-id="1a95b-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="1a95b-152">**ProcessSet**</span></span>
- <span data-ttu-id="1a95b-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="1a95b-153">**Registry**</span></span>
- <span data-ttu-id="1a95b-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="1a95b-154">**Script**</span></span>
- <span data-ttu-id="1a95b-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="1a95b-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="1a95b-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="1a95b-156">**WindowsProcess**</span></span>
- <span data-ttu-id="1a95b-157">**WaitForAll**. Vedere [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="1a95b-158">**WaitForAny**. Vedere [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="1a95b-159">**WaitForSome**. Vedere [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1a95b-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="1a95b-160">Risorse parzialmente funzionanti</span><span class="sxs-lookup"><span data-stu-id="1a95b-160">Resources that are partially functional</span></span>
- <span data-ttu-id="1a95b-161">**Gruppo**</span><span class="sxs-lookup"><span data-stu-id="1a95b-161">**Group**</span></span>
- <span data-ttu-id="1a95b-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="1a95b-162">**GroupSet**</span></span>

  <span data-ttu-id="1a95b-163">**Problema:** le risorse indicate sopra non funzionano se l'istanza specifica viene chiamata due volte, vale a dire se la stessa configurazione viene eseguita due volte</span><span class="sxs-lookup"><span data-stu-id="1a95b-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="1a95b-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="1a95b-164">**Service**</span></span>
- <span data-ttu-id="1a95b-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="1a95b-165">**ServiceSet**</span></span>

  <span data-ttu-id="1a95b-166">**Problema:** funziona solo per l'avvio/arresto del servizio (stato).</span><span class="sxs-lookup"><span data-stu-id="1a95b-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="1a95b-167">Non funziona se si tenta di modificare altri attributi del servizi, come startuptype, credentials, description e così via.</span><span class="sxs-lookup"><span data-stu-id="1a95b-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="1a95b-168">L'errore generato è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="1a95b-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="1a95b-169">*Impossibile trovare il tipo [management.managementobject]: verificare che l'assembly contenente questo tipo sia caricato.*</span><span class="sxs-lookup"><span data-stu-id="1a95b-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="1a95b-170">Risorse non funzionanti</span><span class="sxs-lookup"><span data-stu-id="1a95b-170">Resources that are not functional</span></span>
- <span data-ttu-id="1a95b-171">**User**</span><span class="sxs-lookup"><span data-stu-id="1a95b-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="1a95b-172">Funzionalità DSC non disponibili su Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a95b-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="1a95b-173">Le funzionalità DSC seguenti sono attualmente non disponibili in Nano Server:</span><span class="sxs-lookup"><span data-stu-id="1a95b-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="1a95b-174">Decrittografia del documento MOF con password crittografate</span><span class="sxs-lookup"><span data-stu-id="1a95b-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="1a95b-175">Server di pull: attualmente non è possibile impostare un server di pull su Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a95b-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="1a95b-176">Tutte le funzioni non presenti nel relativo elenco sono disponibili</span><span class="sxs-lookup"><span data-stu-id="1a95b-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="1a95b-177">Uso di risorse DSC personalizzate su Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a95b-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="1a95b-178">A causa di un set limitato di API Windows e alle librerie CLR disponibili in Nano Server, le risorse DSC che funzionano sulla versione CLR completa di Windows non funzionano necessariamente anche su Nano server.</span><span class="sxs-lookup"><span data-stu-id="1a95b-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="1a95b-179">Eseguire un test completo prima di distribuire le risorse DSC personalizzate in un ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="1a95b-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a95b-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1a95b-180">See Also</span></span>

- [<span data-ttu-id="1a95b-181">Guida introduttiva a Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a95b-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
