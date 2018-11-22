---
ms.date: 11/06/2018
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: Utilizzo di PSRepositories locale
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619208"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="9268b-103">Uso dei repository PowerShellGet locali</span><span class="sxs-lookup"><span data-stu-id="9268b-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="9268b-104">I repository di supporto di modulo PowerShellGet diverso da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9268b-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="9268b-105">Questi cmdlet consentono gli scenari seguenti:</span><span class="sxs-lookup"><span data-stu-id="9268b-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="9268b-106">Supportano un set affidabile e pre-convalidato dei moduli di PowerShell per l'uso nell'ambiente in uso</span><span class="sxs-lookup"><span data-stu-id="9268b-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="9268b-107">Una pipeline CI/CD che compila i moduli di PowerShell o script di test</span><span class="sxs-lookup"><span data-stu-id="9268b-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="9268b-108">Distribuire moduli e script di PowerShell per i sistemi che non è possibile accedere a internet</span><span class="sxs-lookup"><span data-stu-id="9268b-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="9268b-109">Questo articolo descrive come configurare un repository di PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="9268b-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="9268b-110">L'articolo riguarda anche il [OfflinePowerShellGetDeploy][] modulo da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9268b-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="9268b-111">Questo modulo contiene i cmdlet per installare la versione più recente di PowerShellGet nel repository locale.</span><span class="sxs-lookup"><span data-stu-id="9268b-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="9268b-112">Tipi di repository locale</span><span class="sxs-lookup"><span data-stu-id="9268b-112">Local repository types</span></span>

<span data-ttu-id="9268b-113">Esistono due modi per creare un PSRepository locale: condivisione di file o server NuGet.</span><span class="sxs-lookup"><span data-stu-id="9268b-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="9268b-114">Ogni tipo presenta vantaggi e svantaggi:</span><span class="sxs-lookup"><span data-stu-id="9268b-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="9268b-115">Server NuGet</span><span class="sxs-lookup"><span data-stu-id="9268b-115">NuGet Server</span></span>

| <span data-ttu-id="9268b-116">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="9268b-116">Advantages</span></span>| <span data-ttu-id="9268b-117">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="9268b-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="9268b-118">Simula strettamente la funzionalità di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="9268b-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="9268b-119">App a più livelli richiede operazioni di pianificazione e supporto</span><span class="sxs-lookup"><span data-stu-id="9268b-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="9268b-120">NuGet si integra con Visual Studio, altri strumenti</span><span class="sxs-lookup"><span data-stu-id="9268b-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="9268b-121">Modello di autenticazione e gestione degli account NuGet necessita</span><span class="sxs-lookup"><span data-stu-id="9268b-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="9268b-122">NuGet supporta i metadati in `.Nupkg` pacchetti</span><span class="sxs-lookup"><span data-stu-id="9268b-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="9268b-123">La pubblicazione richiede la manutenzione e gestione delle chiavi API</span><span class="sxs-lookup"><span data-stu-id="9268b-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="9268b-124">Offre ricerca amministrazione dei pacchetti, e così via.</span><span class="sxs-lookup"><span data-stu-id="9268b-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="9268b-125">Condivisione file</span><span class="sxs-lookup"><span data-stu-id="9268b-125">File Share</span></span>

| <span data-ttu-id="9268b-126">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="9268b-126">Advantages</span></span>| <span data-ttu-id="9268b-127">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="9268b-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="9268b-128">Facile da configurare, eseguire il backup e gestire</span><span class="sxs-lookup"><span data-stu-id="9268b-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="9268b-129">I metadati utilizzati da PowerShellGet non sono disponibili</span><span class="sxs-lookup"><span data-stu-id="9268b-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="9268b-130">Modello di sicurezza semplice - le autorizzazioni utente per la condivisione</span><span class="sxs-lookup"><span data-stu-id="9268b-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="9268b-131">Nessuna interfaccia utente di là di condivisione file di base</span><span class="sxs-lookup"><span data-stu-id="9268b-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="9268b-132">Senza vincoli, ad esempio sostituendo gli elementi esistenti</span><span class="sxs-lookup"><span data-stu-id="9268b-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="9268b-133">Nessuna registrazione di chi Aggiorna cosa e sicurezza limitata</span><span class="sxs-lookup"><span data-stu-id="9268b-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="9268b-134">PowerShellGet funziona con tipo e supporta l'individuazione delle versioni e installazione delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="9268b-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="9268b-135">Tuttavia, alcune funzionalità che funzionano per PowerShell Gallery non sono disponibili per i server NuGet base o le condivisioni file.</span><span class="sxs-lookup"><span data-stu-id="9268b-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="9268b-136">Tutto ciò che è un pacchetto - alcuna differenza di script, moduli, risorse DSC o le funzionalità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="9268b-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="9268b-137">Condivisione di file server non possono visualizzare i metadati del pacchetto, inclusi tag.</span><span class="sxs-lookup"><span data-stu-id="9268b-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="9268b-138">Creazione di un repository locale</span><span class="sxs-lookup"><span data-stu-id="9268b-138">Creating a local repository</span></span>

<span data-ttu-id="9268b-139">L'articolo seguente elenca i passaggi per la configurazione di NuGet Server personalizzato.</span><span class="sxs-lookup"><span data-stu-id="9268b-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="9268b-140">[NuGet. Server][]</span><span class="sxs-lookup"><span data-stu-id="9268b-140">[NuGet.Server][]</span></span>

<span data-ttu-id="9268b-141">Seguire i passaggi fino al momento dell'aggiunta di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="9268b-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="9268b-142">I passaggi per la [pubblicazione di un pacchetto](#publishing-to-a-local-repository) sono trattati più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="9268b-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="9268b-143">Per un repository basato su condivisione file, assicurarsi che gli utenti dispongano delle autorizzazioni per accedere alla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="9268b-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="9268b-144">La registrazione di un repository locale</span><span class="sxs-lookup"><span data-stu-id="9268b-144">Registering a local repository</span></span>

<span data-ttu-id="9268b-145">Prima di poter usare un repository, è necessario registrarlo con il `Register-PSRepository` comando.</span><span class="sxs-lookup"><span data-stu-id="9268b-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="9268b-146">Negli esempi seguenti, il **InstallationPolicy** è impostata su *attendibile*, presupponendo che si ritiene attendibile il proprio repository.</span><span class="sxs-lookup"><span data-stu-id="9268b-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="9268b-147">Prendere nota della differenza tra in che modo i due comandi gestiscono **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="9268b-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="9268b-148">Per un repository basato su condivisione file, il **SourceLocation** e **ScriptSourceLocation** devono corrispondere.</span><span class="sxs-lookup"><span data-stu-id="9268b-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="9268b-149">Per un repository basato sul web, deve essere diversi, quindi in questo esempio una parentesi finale "/" viene aggiunto per il **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="9268b-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="9268b-150">Se si desidera PSRepository appena creato sia il repository predefinito, è necessario annullare la registrazione di tutte le altre PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="9268b-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="9268b-151">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9268b-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="9268b-152">Il nome del repository 'PSGallery' è riservato per l'uso da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9268b-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="9268b-153">È possibile annullare la registrazione PSGallery, ma non è possibile riutilizzare il nome PSGallery per un altro repository.</span><span class="sxs-lookup"><span data-stu-id="9268b-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="9268b-154">Se si vuole ripristinare PSGallery, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9268b-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="9268b-155">Pubblicazione in un repository locale</span><span class="sxs-lookup"><span data-stu-id="9268b-155">Publishing to a local repository</span></span>

<span data-ttu-id="9268b-156">Dopo aver registrato PSRepository locale, è possibile pubblicare nel PSRepository locale.</span><span class="sxs-lookup"><span data-stu-id="9268b-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="9268b-157">Esistono due scenari principali di pubblicazione: il proprio modulo di pubblicazione e pubblicazione di un modulo da PSGallery.</span><span class="sxs-lookup"><span data-stu-id="9268b-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="9268b-158">Pubblicazione di un modulo che è stato creato</span><span class="sxs-lookup"><span data-stu-id="9268b-158">Publishing a module you authored</span></span>

<span data-ttu-id="9268b-159">Uso `Publish-Module` e `Publish-Script` per pubblicare un modulo di PSRepository locale la stessa procedura valida per PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9268b-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="9268b-160">Specificare il percorso per il codice</span><span class="sxs-lookup"><span data-stu-id="9268b-160">Specify the location for your code</span></span>
- <span data-ttu-id="9268b-161">Specificare una chiave API</span><span class="sxs-lookup"><span data-stu-id="9268b-161">Supply an API key</span></span>
- <span data-ttu-id="9268b-162">Specificare il nome del repository.</span><span class="sxs-lookup"><span data-stu-id="9268b-162">Specify the repository name.</span></span> <span data-ttu-id="9268b-163">Ad esempio, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="9268b-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="9268b-164">È necessario creare un account nel server NuGet, quindi accedi per generare e salvare la chiave API.</span><span class="sxs-lookup"><span data-stu-id="9268b-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="9268b-165">Per una condivisione file, utilizzare qualsiasi stringa non vuota per il valore di chiave NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="9268b-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="9268b-166">Di seguito sono riportati alcuni esempi.</span><span class="sxs-lookup"><span data-stu-id="9268b-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="9268b-167">Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script.</span><span class="sxs-lookup"><span data-stu-id="9268b-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="9268b-168">Usare un sistema di gestione sicura delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="9268b-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="9268b-169">Pubblicazione di un modulo da PSGallery</span><span class="sxs-lookup"><span data-stu-id="9268b-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="9268b-170">Per pubblicare un modulo da PSGallery il PSRepository locale, è possibile usare il cmdlet 'Save-Package'.</span><span class="sxs-lookup"><span data-stu-id="9268b-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="9268b-171">Specificare il nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="9268b-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="9268b-172">Specificare 'NuGet' come il Provider</span><span class="sxs-lookup"><span data-stu-id="9268b-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="9268b-173">Specificare il percorso PSGallery come il (di origine https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="9268b-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="9268b-174">Specificare il percorso nel repository locale</span><span class="sxs-lookup"><span data-stu-id="9268b-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="9268b-175">Esempio:</span><span class="sxs-lookup"><span data-stu-id="9268b-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="9268b-176">Se il PSRepository locale è basata sul web, è necessaria un passaggio aggiuntivo che usa nuget.exe da pubblicare.</span><span class="sxs-lookup"><span data-stu-id="9268b-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="9268b-177">Vedere la documentazione per l'utilizzo [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="9268b-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="9268b-178">Installazione PowerShellGet su un sistema disconnesso</span><span class="sxs-lookup"><span data-stu-id="9268b-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="9268b-179">Distribuzione di PowerShellGet è difficile in ambienti che richiedono i sistemi per essere disconnesso da internet.</span><span class="sxs-lookup"><span data-stu-id="9268b-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="9268b-180">PowerShellGet è disponibile un processo bootstrap che installa la prima volta che viene usata la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="9268b-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="9268b-181">Il modulo OfflinePowerShellGetDeploy in PowerShell Gallery include cmdlet che supportano questo processo di bootstrap.</span><span class="sxs-lookup"><span data-stu-id="9268b-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="9268b-182">Per avviare una distribuzione non in linea, è necessario:</span><span class="sxs-lookup"><span data-stu-id="9268b-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="9268b-183">Scaricare e installare il sistema OfflinePowerShellGetDeploy la connessione a internet e i sistemi disconnessi</span><span class="sxs-lookup"><span data-stu-id="9268b-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="9268b-184">Download di PowerShellGet e le relative dipendenze nel sistema connesso a internet usando i `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="9268b-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="9268b-185">Copiare PowerShellGet e le relative dipendenze dal sistema connesso a internet nel disconnesso System</span><span class="sxs-lookup"><span data-stu-id="9268b-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="9268b-186">Usare il `Install-PowerShellGetOffline` nel disconnesso sistema inserisca PowerShellGet e le relative dipendenze nelle cartelle appropriate</span><span class="sxs-lookup"><span data-stu-id="9268b-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="9268b-187">I comandi seguenti usano `Save-PowerShellGetForOffline` inserire tutti i componenti in una cartella `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="9268b-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="9268b-188">A questo punto, è necessario rendere il contenuto di `F:\OfflinePowerShellGet` disponibile per i sistemi disconnessi.</span><span class="sxs-lookup"><span data-stu-id="9268b-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="9268b-189">Eseguire il `Install-PowerShellGetOffline` cmdlet per installare PowerShellGet nel disconnesso sistema.</span><span class="sxs-lookup"><span data-stu-id="9268b-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="9268b-190">È importante che non è eseguito PowerShellGet nella sessione di PowerShell prima di eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="9268b-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="9268b-191">Una volta PowerShellGet è caricato nella sessione, non è possibile aggiornare i componenti.</span><span class="sxs-lookup"><span data-stu-id="9268b-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="9268b-192">Se si avvia PowerShellGet per errore, chiudere e riavviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9268b-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="9268b-193">Dopo aver eseguito questi comandi, si è pronti a pubblicare PowerShellGet nel repository locale.</span><span class="sxs-lookup"><span data-stu-id="9268b-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="9268b-194">Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script.</span><span class="sxs-lookup"><span data-stu-id="9268b-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="9268b-195">Usare un sistema di gestione sicura delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="9268b-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[NuGet. Server]: /nuget/hosting-packages/nuget-server
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[NuGet.exe]: /nuget/tools/nuget-exe-cli-reference
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference