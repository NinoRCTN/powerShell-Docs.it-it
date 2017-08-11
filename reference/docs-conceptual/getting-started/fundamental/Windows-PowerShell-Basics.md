---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Nozioni di base su Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: f8a520f1fbe97737c7d0c2acab0129f88b5ed425
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-basics"></a>Nozioni di base su Windows PowerShell
Le interfacce utente grafiche usano alcuni concetti di base ben noti alla maggior parte degli utenti di computer. Gli utenti contano sulla familiarità di tali interfacce per eseguire le attività. I sistemi operativi offrono agli utenti una rappresentazione grafica degli elementi che possono essere visualizzati, in genere con menu a discesa per l'accesso a funzionalità specifiche e menu di scelta rapida per l'accesso a funzionalità specifiche di un determinato contesto.

Un'interfaccia della riga di comando (CLI) come Windows PowerShell, deve usare un approccio diverso per esporre le informazioni, perché non sono disponibili menu o sistemi grafici di aiuto all'utente. È necessario conoscere i nomi dei comandi per poterli usare. Anche se è possibile digitare comandi complessi equivalenti alle funzionalità in un ambiente GUI, è necessario acquisire familiarità con i comandi e i parametri di comando usati comunemente.

La maggior parte delle interfacce della riga di comando non include schemi o modelli che possano aiutare l'utente a imparare l'interfaccia. Trattandosi delle prime shell di sistema operativo, molti nomi di comandi e di parametri delle interfacce della riga di comando sono stati selezionati in modo arbitrario, privilegiando in genere la sinteticità rispetto alla chiarezza. Anche se nella maggior parte delle interfacce della riga di comando sono integrati sistemi di Guida e standard di progettazione dei comandi, si tratta in genere di comandi progettati per la compatibilità con i comandi precedenti, quindi il set di comandi rispecchia ancora decisioni prese decenni fa.

Windows PowerShell è stato progettato per sfruttare le conoscenze storiche delle interfacce della riga di comando degli utenti. In questo capitolo verranno presentati alcuni strumenti e concetti di base utili per acquisire rapidamente familiarità con Windows PowerShell. Tali impostazioni includono:

-   Uso di Get-Command

-   Uso di Cmd.exe e dei comandi UNIX

-   Uso di comandi esterni

-   Uso di Tab-Completion

-   Uso di Get-Help
