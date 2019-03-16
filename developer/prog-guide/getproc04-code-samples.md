---
title: Esempi di codice GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054646"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="3e8b1-102">Codici di esempio di GetProc04</span><span class="sxs-lookup"><span data-stu-id="3e8b1-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="3e8b1-103">Ecco gli esempi di codice per il cmdlet di esempio GetProc04.</span><span class="sxs-lookup"><span data-stu-id="3e8b1-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="3e8b1-104">Questo è il `Get-Process` cmdlet esempio descritto in [aggiunta non fatali di segnalazione errori per il Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="3e8b1-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="3e8b1-105">Ciò `Get-Process` le chiamate di cmdlet di [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo ogni volta che viene generata un'eccezione di operazione non valida durante il recupero delle informazioni sul processo.</span><span class="sxs-lookup"><span data-stu-id="3e8b1-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="3e8b1-106">È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-Process tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="3e8b1-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3e8b1-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3e8b1-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3e8b1-108">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="3e8b1-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="3e8b1-109">Per il codice di esempio completo, vedere gli argomenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="3e8b1-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="3e8b1-110">Language</span><span class="sxs-lookup"><span data-stu-id="3e8b1-110">Language</span></span>|<span data-ttu-id="3e8b1-111">Argomento</span><span class="sxs-lookup"><span data-stu-id="3e8b1-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="3e8b1-112">C#</span><span class="sxs-lookup"><span data-stu-id="3e8b1-112">C#</span></span>|[<span data-ttu-id="3e8b1-113">GetProc04 (C#) esempi di codice</span><span class="sxs-lookup"><span data-stu-id="3e8b1-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="3e8b1-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="3e8b1-114">VB.NET</span></span>|[<span data-ttu-id="3e8b1-115">GetProc04 codice di esempio (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="3e8b1-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="3e8b1-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3e8b1-116">See Also</span></span>

[<span data-ttu-id="3e8b1-117">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e8b1-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3e8b1-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3e8b1-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)