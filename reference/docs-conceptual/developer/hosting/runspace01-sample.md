---
title: Esempio Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367420"
---
# <a name="runspace01-sample"></a>Esempio di Runspace01

Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono. Il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce gli oggetti [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) per ogni processo in esecuzione nel computer locale. I valori delle proprietà [System. Diagnostics. Process. ProcessName *](/dotnet/api/System.Diagnostics.Process.ProcessName) e [System. Diagnostics. Process. HandleCount *](/dotnet/api/System.Diagnostics.Process.Handlecount) vengono quindi estratti dagli oggetti restituiti e visualizzati in una finestra della console.

## <a name="requirements"></a>Requisiti

 Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustra

- Creazione di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire un comando.

- Aggiunta di un comando alla pipeline dell'oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Esecuzione del comando in modo sincrono.

- Uso di oggetti [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) per estrarre le proprietà dagli oggetti restituiti dal comando.

## <a name="example"></a>Esempio

 Questo esempio esegue il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono nei spazio predefiniti forniti da Windows PowerShell.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Vedere anche
