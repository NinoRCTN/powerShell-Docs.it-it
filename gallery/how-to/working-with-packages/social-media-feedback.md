---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Pubblicazione di feedback sui social media o nei commenti
ms.openlocfilehash: a7cdcc2ff2c18fb606d077adf0bdecf57c90703f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003762"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="bae6e-103">Pubblicazione di feedback sui social media o nei commenti</span><span class="sxs-lookup"><span data-stu-id="bae6e-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="bae6e-104">Powershell Gallery supporta due approcci per gli utenti che vogliono offrire commenti e suggerimenti pubblici su un pacchetto:</span><span class="sxs-lookup"><span data-stu-id="bae6e-104">The Powershell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="bae6e-105">Usare i collegamenti sul lato sinistro per condividere un pacchetto su siti di social media quali Twitter, LinkedIn o Facebook.</span><span class="sxs-lookup"><span data-stu-id="bae6e-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="bae6e-106">Usare la funzionalità dei commenti per inviare commenti su un pacchetto e consentire agli autori di monitorare i commenti sui pacchetti che pubblicano.</span><span class="sxs-lookup"><span data-stu-id="bae6e-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="bae6e-107">Commenti e suggerimenti sui social media</span><span class="sxs-lookup"><span data-stu-id="bae6e-107">Social Media Feedback</span></span>

<span data-ttu-id="bae6e-108">Per ogni pacchetto di PowerShell Gallery, sul lato sinistro della pagina sono disponibili collegamenti a Facebook, LinkedIn e Twitter.</span><span class="sxs-lookup"><span data-stu-id="bae6e-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="bae6e-109">Se si fa clic su tali collegamenti viene aperto il sito di uno dei social media, ed è possibile condividere rapidamente un collegamento al pacchetto.</span><span class="sxs-lookup"><span data-stu-id="bae6e-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="bae6e-110">Gli utenti devono eseguire l'accesso al sito che hanno scelto per condividere il pacchetto di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="bae6e-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="bae6e-111">Gli utenti sono invitati a eseguire questa operazione se pensano di consigliare un pacchetto ad altri utenti.</span><span class="sxs-lookup"><span data-stu-id="bae6e-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="bae6e-112">PowerShell Gallery verifica tutte le condivisioni di un dato pacchetto sui social media e visualizza il numero di volte in cui il pacchetto è stato condiviso in ognuno di essi.</span><span class="sxs-lookup"><span data-stu-id="bae6e-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="bae6e-113">Poiché tale indicazione visualizza solo il numero di volte in cui un pacchetto è stato condiviso, verrà interpretata dagli altri utenti come il numero di "like" del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="bae6e-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the package.</span></span>


## <a name="comments"></a><span data-ttu-id="bae6e-114">Commenti</span><span class="sxs-lookup"><span data-stu-id="bae6e-114">Comments</span></span>

<span data-ttu-id="bae6e-115">PowerShell Gallery usa il servizio LiveFyre per consentire agli utenti di inviare commenti sui pacchetti.</span><span class="sxs-lookup"><span data-stu-id="bae6e-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="bae6e-116">Gli utenti che vogliono inviare consigli o commenti possono usare questa funzionalità per offrire commenti e suggerimenti visibili a chiunque visiti la pagina del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="bae6e-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="bae6e-117">I proprietari del pacchetto possono seguire questi commenti e suggerimenti e riceveranno una notifica quando un utente inserisce un commento.</span><span class="sxs-lookup"><span data-stu-id="bae6e-117">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="bae6e-118">Il sistema dei commenti è basato su LiveFyre, un servizio separato che non è gestito da Microsoft e richiede un account di accesso univoco.</span><span class="sxs-lookup"><span data-stu-id="bae6e-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="bae6e-119">La prima volta che si vuole lasciare un commento o seguire i commenti in uno dei pacchetti, verrà richiesto di creare un account LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="bae6e-119">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="bae6e-120">Se è stato creato un account LiveFyre e si è eseguito l'accesso, è possibile elaborare un commento per offrire commenti e suggerimenti sul pacchetto e fare clic su "Post comment..." (Pubblica commento). Il commento non sarà visibile immediatamente.</span><span class="sxs-lookup"><span data-stu-id="bae6e-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="bae6e-121">I commenti per i pacchetti della raccolta vengono moderati dagli amministratori di PowerShell Gallery e tutti i post vengono rivisti dai moderatori prima di venire pubblicati ed essere visibili ad altri utenti.</span><span class="sxs-lookup"><span data-stu-id="bae6e-121">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="bae6e-122">Lo scopo di moderare i commenti è garantire che siano allineati con il comportamento pubblico in base a quanto contenuto nelle [Condizioni per l'utilizzo](https://www.powershellgallery.com/policies/Terms) di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="bae6e-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="bae6e-123">I proprietari dei pacchetti sono invitati a seguire i commenti inviati a LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="bae6e-123">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="bae6e-124">È necessario un account LiveFyre ed è consigliabile usare lo stesso indirizzo di posta elettronica usato per pubblicare il pacchetto in LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="bae6e-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="bae6e-125">Per seguire i commenti, accedere a LiveFyre e passare a qualsiasi pacchetto per cui si è elencati come proprietari.</span><span class="sxs-lookup"><span data-stu-id="bae6e-125">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="bae6e-126">Sotto la casella dei commenti, nella parte inferiore di ogni pacchetto viene visualizzato "+Follow" (Segui).</span><span class="sxs-lookup"><span data-stu-id="bae6e-126">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="bae6e-127">Quando si fa clic su questa opzione, LiveFyre invia un messaggio di posta elettronica all'indirizzo registrato ogni volta in cui vengono aggiunti nuovi commenti per il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="bae6e-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>