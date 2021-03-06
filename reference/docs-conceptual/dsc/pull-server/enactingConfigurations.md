---
ms.date: 10/16/2017
keywords: dsc,powershell,configurazione,installazione
title: Applicazione delle configurazioni
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953648"
---
# <a name="enacting-configurations"></a>Applicazione delle configurazioni

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Ci sono due modi per applicare le configurazioni di PowerShell DSC (Desired State Configuration): la modalità push e la modalità pull.

## <a name="push-mode"></a>Modalità push

![Modalità push](../images/pushModel.png "Come funziona la modalità push")

La modalità push fa riferimento a un utente che applica attivamente una configurazione in un nodo di destinazione chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

Dopo la creazione e la compilazione di una configurazione, è possibile applicarla in modalità push chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration), impostando il parametro -Path del cmdlet sul percorso in cui si trova il file MOF di configurazione.
Se, ad esempio, il file MOF di configurazione si trova in `C:\DSC\Configurations\localhost.mof`, per applicarlo al computer locale usare il comando seguente: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Nota__: per impostazione predefinita, DSC esegue una configurazione come processo in background. Per eseguire la configurazione in modo interattivo, chiamare [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) con il parametro __-Wait__.

## <a name="pull-mode"></a>Modalità pull

![Modalità pull](../images/pullModel.png "Come funziona la modalità pull")

In modalità pull, i client di pull sono configurati per ottenere le relative configurazioni DSC da un servizio di pull remoto.
Analogamente, il servizio di pull è stato configurato per ospitare il servizio DSC e ne è stato effettuato il provisioning con le configurazioni e le risorse richieste dai client di pull.
Ogni client di pull ha un evento pianificato che esegue un controllo di conformità periodico sulla configurazione del nodo.
Quando l'evento viene generato per la prima volta, Gestione configurazione locale nel client di pull effettua una richiesta al servizio di pull per ottenere la configurazione specificata in Gestione configurazione locale.
Se tale configurazione è disponibile nel servizio di pull e supera i controlli di convalida iniziali, viene scaricata nel client di pull, dove viene quindi eseguita da Gestione configurazione locale.

Gestione configurazione locale verifica che il client sia conforme alla configurazione a intervalli regolari, come specificato dalla proprietà **ConfigurationModeFrequencyMins** di Gestione configurazione locale.
Gestione configurazione locale verifica se sono disponibili configurazioni aggiornate nel servizio di pull a intervalli regolari, come specificato dalla proprietà **RefreshModeFrequency** di Gestione configurazione locale.
Per informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).

La soluzione consigliata per l'hosting di un servizio di pull è il servizio cloud DSC, ovvero [Automazione di Azure](https://azure.microsoft.com/services/automation/).
Questa soluzione ospitata offre funzionalità di gestione con interfaccia grafica, creazione di report e amministrazione centralizzata.

Per altre informazioni sulla configurazione di un servizio di pull in Windows Server, vedere [Configurazione di un server di pull Web DSC](pullServer.md).
Tenere presente, tuttavia, che questa implementazione offre funzionalità limitate e richiede alcuni interventi di integrazione manuali.

Gli argomenti seguenti illustrano il servizio e i client di pull:

- [Panoramica della piattaforma DSC di Automazione di Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configurazione di un server di pull SMB](pullServerSMB.md)
- [Configurazione di un client di pull](pullClientConfigID.md)
