---
title: Come richiedere le conferme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369680"
---
# <a name="how-to-request-confirmations"></a>Come richiedere conferme

Questo esempio illustra come chiamare i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) per richiedere le conferme dell'utente prima che venga eseguita un'azione.

> [!IMPORTANT]
> Per ulteriori informazioni sul modo in cui Windows PowerShell gestisce queste richieste, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Per richiedere la conferma

1. Verificare che il parametro `SupportsShouldProcess` dell'attributo cmdlet sia impostato su `true`. (Per le funzioni si tratta di un parametro dell'attributo di cmdlet.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Aggiungere un parametro `Force` al cmdlet in modo che l'utente possa eseguire l'override di una richiesta di conferma.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Aggiungere un'istruzione `if` che usa il valore restituito del metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) per determinare se viene chiamato il metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) .

4. Aggiungere una seconda istruzione `if` che usa il valore restituito del metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e il valore del parametro `Force` per determinare se l'operazione deve essere eseguita.

## <a name="example"></a>Esempio

Nell'esempio di codice seguente, i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) vengono chiamati dall'interno dell'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . È tuttavia possibile chiamare questi metodi anche dagli altri metodi di elaborazione degli input.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
