---
title: GetProc03 (C#) esempi di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: c24d18a2b80f8f9b62b5418fed35f54f7c7da23c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855407"
---
# <a name="getproc03-c-sample-code"></a>Codice di esempio di GetProc03 (C#)

Il codice seguente viene illustrata l'implementazione di un `Get-Process` cmdlet in grado di accettare le pipeline di input. Questa implementazione definisce una `Name` parametro che accetta l'input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi specificati e Usa quindi il [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodo come meccanismo di output per l'invio di oggetti alla pipeline.

> [!NOTE]
> È possibile scaricare il C# file di origine (getprov03.cs) per questo cmdlet Get-Process tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> È possibile scaricare il C# file di origine (getprov03.cs) per questo cmdlet Get-Process tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)