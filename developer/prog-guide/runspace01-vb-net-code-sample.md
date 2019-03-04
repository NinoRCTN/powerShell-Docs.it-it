---
title: Runspace01 esempio di codice (Visual Basic.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12ee5382-95ba-41c7-8291-7f69a6f63514
caps.latest.revision: 7
ms.openlocfilehash: fbc90a6736d841fe184b86ab143809ad23c7977a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856057"
---
# <a name="runspace01-vbnet-code-sample"></a>Codice di esempio di Runspace01 (VB.NET)

Ecco gli esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). A tale scopo, l'applicazione richiama uno spazio di esecuzione e quindi richiama un comando. Si noti che questa applicazione non specifica le informazioni di configurazione dello spazio di esecuzione, né e in modo esplicito crea una pipeline. Il comando che viene richiamato il `Get-Process` cmdlet.
Ecco gli esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). A tale scopo, l'applicazione richiama uno spazio di esecuzione e quindi richiama un comando. Si noti che questa applicazione non specifica le informazioni di configurazione dello spazio di esecuzione, né e in modo esplicito crea una pipeline. Il comando che viene richiamato il `Get-Process` cmdlet.

## <a name="code-sample"></a>Esempio di codice

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)