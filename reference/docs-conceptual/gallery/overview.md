---
ms.date: 06/12/2017
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327862"
---
# <a name="the-powershell-gallery"></a>PowerShell Gallery

PowerShell Gallery è il repository centrale per i contenuti PowerShell. Al suo interno è possibile trovare utili moduli di PowerShell che contengono comandi di PowerShell o risorse DSC (Desired State Configuration).
Sono anche disponibili script di PowerShell, alcuni dei quali possono contenere flussi di lavoro di PowerShell e descrivono e stabiliscono la sequenza di un set di attività. Alcuni di questi pacchetti sono creati da Microsoft, altri dalla community di PowerShell.

## <a name="powershellget-overview"></a>Panoramica di PowerShellGet

Il modulo PowerShellGet contiene i cmdlet per l'individuazione, l'installazione, l'aggiornamento e la pubblicazione di pacchetti di PowerShell che contengono artefatti come moduli, risorse DSC, capacità del ruolo e script da [PowerShell Gallery](https://www.PowerShellGallery.com) e altri repository privati.

## <a name="getting-started-with-the-gallery"></a>Introduzione a PowerShell Gallery

L'installazione di pacchetti da PowerShell Gallery richiede la versione più recente del modulo PowerShellGet.
Per istruzioni complete, vedere [Installazione di PowerShellGet](installing-psget.md).

Per altre informazioni su come usare i comandi PowerShellGet con PowerShell Gallery, consultare la pagina [Introduzione](getting-started.md). È inoltre possibile eseguire *Update-Help -Module PowerShellGet* per installare la Guida locale per tali comandi.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati

Il modulo **PowerShellGet** richiede **Windows PowerShell 3.0 o versione successiva** o **PowerShell Core 6.0 o versione successiva**.

È disponibile una versione appropriata di **Windows PowerShell** per questi sistemi operativi:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** richiede .NET Framework 4.5 o versione successiva. È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/library/5a4x27ek.aspx).

Poiché **PowerShell Core** è multipiattaforma e questo significa che funziona in Windows, Linux e MacOS, anche **PowerShellGet** è disponibile in tali sistemi. Per un elenco completo dei sistemi supportati da **PowerShell Core** vedere [Installazione di varie versioni di PowerShell](/powershell/scripting/setup/installing-powershell).

Molti moduli ospitati nella raccolta supporteranno sistemi operativi diversi e hanno requisiti aggiuntivi. Per altre informazioni, vedere la documentazione per i moduli.

## <a name="got-a-question-have-feedback"></a>Domande? Commenti e suggerimenti?

Altre informazioni su PowerShell Gallery e PowerShellGet sono disponibili nella pagina [Introduzione](getting-started.md). Fornire commenti e suggerimenti e segnalare problemi usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
