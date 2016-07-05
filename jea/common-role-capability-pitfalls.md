---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "problemi comuni delle capacità del ruolo"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### Problemi comuni delle capacità del ruolo
È possibile incorrere in alcuni inconvenienti durante il processo.
Questa guida rapida illustra come identificare e risolvere tali inconvenienti quando si modifica o si crea un nuovo endpoint:

#### Funzioni e Cmdlet
I comandi di PowerShell scritti in PowerShell sono funzioni di PowerShell.
I comandi di PowerShell scritti come classi .NET specializzate sono cmdlet di PowerShell.
È possibile verificare il tipo di comando eseguendo `Get-Command`.

#### VisibleProviders
È necessario esporre qualsiasi provider richiesto dai comandi.
Il più comune è il provider FileSystem, ma potrebbe essere necessario esporne altri, ad esempio il provider Registry.
Per un'introduzione ai provider, vedere il [post del blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Prestare attenzione quando si espongono i provider: spesso è preferibile definire una propria funzione da usare con i provider sottostanti anziché esporre direttamente il provider in una sessione di JEA.
In questo modo è comunque possibile consentire agli utenti di lavorare con file, chiavi del Registro di sistema e così via, mantenendo tuttavia il controllo su **quali** file e chiavi del Registro di sistema possono essere usati con la logica di convalida personalizzata.




<!--HONumber=Jun16_HO4-->


