---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Sintassi di ricerca di PowerShell Gallery
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003778"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="d24e3-103">Sintassi di ricerca di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d24e3-103">Gallery Search Syntax</span></span>

<span data-ttu-id="d24e3-104">PowerShell Gallery offre una casella di ricerca di testo in cui è possibile usare parole, frasi ed espressioni di parole chiave per restringere i risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="d24e3-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="d24e3-105">Ricerca per parole chiave</span><span class="sxs-lookup"><span data-stu-id="d24e3-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="d24e3-106">La funzionalità di ricerca troverà e restituirà tutti i documenti rilevanti che contengono tutte e 3 le parole chiave.</span><span class="sxs-lookup"><span data-stu-id="d24e3-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="d24e3-107">Ricerca per frasi e parole chiave</span><span class="sxs-lookup"><span data-stu-id="d24e3-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="d24e3-108">Se si immette una frase tra virgolette (""), la modalità di ricerca cambia e viene cercata la specifica frase e non le singole parole chiave.</span><span class="sxs-lookup"><span data-stu-id="d24e3-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="d24e3-109">I documenti corrispondenti in genere contengono la frase esatta "azure sql", incluse le varianti relative alle lettere maiuscole/minuscole, ad esempio "Azure SQL", e la parola 'deployment'.</span><span class="sxs-lookup"><span data-stu-id="d24e3-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="d24e3-110">Filtri relativi ai campi</span><span class="sxs-lookup"><span data-stu-id="d24e3-110">Filtering on fields</span></span>

<span data-ttu-id="d24e3-111">È possibile cercare l'ID (oppure le varianti 'Id' o 'id') di un pacchetto specifico o alcuni altri campi anteponendo il nome del campo ai termini della ricerca.</span><span class="sxs-lookup"><span data-stu-id="d24e3-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="d24e3-112">Attualmente, i campi su cui è possibile eseguire la ricerca sono 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="d24e3-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="d24e3-113">Qual è la differenza tra ID e Title?</span><span class="sxs-lookup"><span data-stu-id="d24e3-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="d24e3-114">ID è il nome usato nella console.</span><span class="sxs-lookup"><span data-stu-id="d24e3-114">ID is the name you use in the console.</span></span> <span data-ttu-id="d24e3-115">Title è ciò che viene visualizzato nella parte superiore della pagina del pacchetto nei risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="d24e3-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="d24e3-116">Esempi</span><span class="sxs-lookup"><span data-stu-id="d24e3-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="d24e3-117">trova i pacchetti con "PSReadline" o "AzureRM.Profile" nei rispettivi campi ID.</span><span class="sxs-lookup"><span data-stu-id="d24e3-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="d24e3-118">è un altro modo per trovare i pacchetti con "AzureRM.Profile" nel campo ID.</span><span class="sxs-lookup"><span data-stu-id="d24e3-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="d24e3-119">Il filtro 'Id' è una corrispondenza della sottostringa, quindi se si cerca:</span><span class="sxs-lookup"><span data-stu-id="d24e3-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="d24e3-120">si ottengono risultati come 'AzureRM.Profile' e 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="d24e3-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="d24e3-121">È possibile cercare anche più parole chiave in un singolo campo.</span><span class="sxs-lookup"><span data-stu-id="d24e3-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="d24e3-122">Oppure combinare e associare i campi.</span><span class="sxs-lookup"><span data-stu-id="d24e3-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="d24e3-123">È anche possibile eseguire ricerche di frasi:</span><span class="sxs-lookup"><span data-stu-id="d24e3-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="d24e3-124">Per cercare tutti i pacchetti con tag DSC.</span><span class="sxs-lookup"><span data-stu-id="d24e3-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="d24e3-125">Per cercare tutti i pacchetti con la funzione specificata.</span><span class="sxs-lookup"><span data-stu-id="d24e3-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="d24e3-126">Per cercare tutti i pacchetti con il cmdlet specificato.</span><span class="sxs-lookup"><span data-stu-id="d24e3-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="d24e3-127">Per cercare tutti i pacchetti con il nome di risorsa DSC specificato.</span><span class="sxs-lookup"><span data-stu-id="d24e3-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="d24e3-128">Per cercare tutti i pacchetti con il valore PowerShellVersion specificato</span><span class="sxs-lookup"><span data-stu-id="d24e3-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="d24e3-129">Infine, se si usa un campo non supportato, ad esempio 'commands', il campo verrà semplicemente ignorato e la ricerca verrà eseguita su tutti i campi.</span><span class="sxs-lookup"><span data-stu-id="d24e3-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="d24e3-130">Quindi, la query seguente</span><span class="sxs-lookup"><span data-stu-id="d24e3-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="d24e3-131">viene interpretata esattamente come questa query:</span><span class="sxs-lookup"><span data-stu-id="d24e3-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage