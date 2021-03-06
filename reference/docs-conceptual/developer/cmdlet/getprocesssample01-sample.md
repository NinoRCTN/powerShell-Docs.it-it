---
title: Esempio GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369730"
---
# <a name="getprocesssample01-sample"></a>Esempio di GetProcessSample01

In questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale. Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Come compilare l'esempio usando Visual Studio.

1. Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample01. Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Fare doppio clic sull'icona del file di soluzione (con estensione sln). Verrà aperto il progetto di esempio in Microsoft Visual Studio.

3. Scegliere **Compila soluzione** dal menu **Compila**.

  La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.

### <a name="how-to-run-the-sample"></a>Per eseguire l'esempio

1. Aprire una finestra del prompt dei comandi.

2. Passare alla directory contenente il file con estensione dll di esempio.

3. Eseguire installutil "GetProcessSample01. dll".

4. Avviare Windows PowerShell.

5. Eseguire il comando seguente per aggiungere lo snap-in alla Shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Immettere il comando seguente per eseguire il cmdlet. `get-proc`

   `get-proc`

   Si tratta di un output di esempio risultante dalla procedura seguente.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 1,0 o versioni successive.

## <a name="demonstrates"></a>Illustra

In questo esempio vengono illustrate le operazioni seguenti.

- Creazione di un cmdlet di esempio di base.

- Definizione di una classe di cmdlet tramite l'attributo cmdlet.

- Creazione di uno snap-in che funziona sia con Windows PowerShell 1,0 che con Windows PowerShell 2,0. Gli esempi successivi usano i moduli anziché gli snap-in in modo che richiedano Windows PowerShell 2,0.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come creare un cmdlet semplice e il relativo snap-in.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)