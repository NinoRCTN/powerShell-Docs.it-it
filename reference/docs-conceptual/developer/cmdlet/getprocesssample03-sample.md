---
title: Esempio GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369710"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="5ac83-102">Esempio di GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="5ac83-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="5ac83-103">In questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="5ac83-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="5ac83-104">Fornisce un `Name` parametro che può accettare un oggetto dalla pipeline o un valore di una proprietà di un oggetto il cui nome di proprietà corrisponde al nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="5ac83-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="5ac83-105">Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="5ac83-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="5ac83-106">Come compilare l'esempio con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5ac83-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="5ac83-107">Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="5ac83-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="5ac83-108">Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="5ac83-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="5ac83-109">Fare doppio clic sull'icona del file di soluzione (con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="5ac83-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="5ac83-110">Verrà aperto il progetto di esempio in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5ac83-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="5ac83-111">Scegliere **Compila soluzione** dal menu **Compila**.</span><span class="sxs-lookup"><span data-stu-id="5ac83-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="5ac83-112">La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.</span><span class="sxs-lookup"><span data-stu-id="5ac83-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="5ac83-113">Per eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="5ac83-113">How to run the sample</span></span>

1. <span data-ttu-id="5ac83-114">Creare la cartella dei moduli seguente:</span><span class="sxs-lookup"><span data-stu-id="5ac83-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="5ac83-115">Copiare l'assembly di esempio nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="5ac83-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="5ac83-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ac83-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="5ac83-117">Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5ac83-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="5ac83-118">Eseguire il comando seguente per eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5ac83-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="5ac83-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5ac83-119">Requirements</span></span>

<span data-ttu-id="5ac83-120">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="5ac83-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5ac83-121">Illustra</span><span class="sxs-lookup"><span data-stu-id="5ac83-121">Demonstrates</span></span>

<span data-ttu-id="5ac83-122">In questo esempio vengono illustrate le operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="5ac83-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="5ac83-123">Dichiarazione di una classe di cmdlet mediante l'attributo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ac83-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="5ac83-124">Dichiarazione di un parametro del cmdlet mediante l'attributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="5ac83-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="5ac83-125">Specifica la posizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="5ac83-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="5ac83-126">Specifica che il parametro accetta input dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5ac83-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="5ac83-127">L'input può essere tratto da un oggetto o da un valore di una proprietà di un oggetto il cui nome di proprietà corrisponde al nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="5ac83-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="5ac83-128">Dichiarazione di un attributo di convalida per l'input del parametro.</span><span class="sxs-lookup"><span data-stu-id="5ac83-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="5ac83-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="5ac83-129">Example</span></span>

<span data-ttu-id="5ac83-130">Questo esempio illustra un'implementazione del cmdlet Get-proc che include un parametro `Name` che accetta l'input dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5ac83-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="5ac83-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ac83-131">See Also</span></span>

[<span data-ttu-id="5ac83-132">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ac83-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
