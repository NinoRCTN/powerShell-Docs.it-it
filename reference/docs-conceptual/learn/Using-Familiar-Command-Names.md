---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Uso di nomi di comandi familiari
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403509"
---
# <a name="using-familiar-command-names"></a>Uso di nomi di comandi familiari

PowerShell supporta l'uso di alias per fare riferimento ai comandi tramite nomi alternativi. L'uso di alias permette agli utenti che hanno esperienza in altre shell di usare i nomi di comando comuni che conoscono già per operazioni simili in PowerShell.

L'uso di alias associa un nuovo nome a un altro comando. Ad esempio, PowerShell include una funzione interna denominata `Clear-Host` che cancella la finestra di output. È possibile digitare l'alias `cls` o `clear` al prompt dei comandi. PowerShell interpreta questi alias ed esegue la funzione `Clear-Host`.

Questa funzionalità semplifica l'apprendimento di PowerShell per gli utenti. Prima di tutto, la maggior parte degli utenti di **cmd.exe** e UNIX ha a disposizione un vasto repertorio di comandi di cui conosce già il nome. Gli equivalenti in PowerShell possono non produrre risultati identici. Tuttavia, i risultati sono sufficientemente simili perché gli utenti possano usarli senza conoscere il nome del comando di PowerShell. La "memoria delle dita" è un'altra importante fonte di frustrazione quando si apprende una nuova shell di comandi. Dopo aver usato **cmd.exe** per anni, si potrebbe digitare in automatico il comando `cls` per cancellare lo schermo. Senza l'alias per `Clear-Host`, si riceverebbe un messaggio di errore e potrebbe non essere chiaro che cosa fare per cancellare l'output.

L'elenco seguente mostra alcuni dei comandi di UNIX e **cmd.exe** comuni che è possibile usare in PowerShell:

|||||
|-|-|-|-|
|cat|dir|montare|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|tipo|
|del|lp|r|write|
|diff|ls|ren||

Il cmdlet `Get-Alias` mostra il vero nome del comando di PowerShell nativo associato a un alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interpretazione di alias standard

Gli alias descritti nella sezione precedente sono stati progettati per la compatibilità dei nomi con altre shell di comandi.
La maggior parte degli alias integrati in PowerShell è progettata per garantire la brevità. Nomi più brevi sono più facili da digitare, ma sono difficili da leggere se non si sa a cosa si riferiscono.

Gli alias di PowerShell stabiliscono un compromesso tra chiarezza e brevità. PowerShell usa un set standard di alias per sostantivi e verbi comuni.

Esempi di abbreviazioni:

| Sostantivo o verbo | Abbreviazione |
|--------------|--------------|
| Get          | g            |
| Imposta          | s            |
| Item         | i            |
| Posizione     | l            |
| Command      | cm           |
| Alias        | al           |

Questi alias sono comprensibili quando si conoscono i nomi abbreviati.

| Nome del cmdlet    | Alias |
|----------------|-------|
| `Get-Item `    | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

Dopo aver acquisito familiarità con gli alias di PowerShell, è facile indovinare che l'alias **sal** si riferisce a `Set-Alias`.

## <a name="creating-new-aliases"></a>Creazione di nuovi alias

È possibile creare alias personalizzati usando il cmdlet `Set-Alias`. Ad esempio, le istruzioni seguenti creano gli alias dei cmdlet standard descritti in precedenza:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente PowerShell usa comandi simili durante l'avvio, ma questi alias non sono modificabili.
Se si prova a eseguire uno di questi comandi, si otterrà un errore che indica che l'alias non può essere modificato. Ad esempio:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```