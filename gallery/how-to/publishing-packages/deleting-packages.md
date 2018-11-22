---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminazione di pacchetti
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003861"
---
# <a name="deleting-packages"></a><span data-ttu-id="1187e-103">Eliminazione di pacchetti</span><span class="sxs-lookup"><span data-stu-id="1187e-103">Deleting Packages</span></span>

<span data-ttu-id="1187e-104">PowerShell Gallery non supporta l'eliminazione permanente di pacchetti perché questo causerebbe interruzioni per altri pacchetti dipendenti.</span><span class="sxs-lookup"><span data-stu-id="1187e-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="1187e-105">PowerShell Gallery supporta invece un modo per 'escludere dall'elenco' un pacchetto, operazione che può essere eseguita nella pagina di gestione del pacchetto nel sito Web.</span><span class="sxs-lookup"><span data-stu-id="1187e-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="1187e-106">Quando un pacchetto viene escluso dall'elenco, non compare più nelle ricerche e non viene visualizzato in nessun elenco di pacchetti, né in PowerShell Gallery né usando i comandi PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="1187e-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="1187e-107">È tuttavia possibile scaricarlo specificandone la versione esatta. Questo consente agli script automatizzati di continuare a funzionare.</span><span class="sxs-lookup"><span data-stu-id="1187e-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="1187e-108">Se si verifica una situazione eccezionale che richiede l'eliminazione di un pacchetto, tale operazione può essere eseguita manualmente dal team di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1187e-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="1187e-109">Una violazione di copyright o la presenza di contenuto potenzialmente dannoso è una ragione valida per procedere all'eliminazione.</span><span class="sxs-lookup"><span data-stu-id="1187e-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="1187e-110">In questo caso, è necessario inviare una richiesta di supporto tramite [PowerShell Gallery](http://www.PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="1187e-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>