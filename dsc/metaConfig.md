---
title:   Configurazione di Gestione configurazione locale
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Configurazione di Gestione configurazione locale

> Si applica a: Windows PowerShell 5.0

Gestione configurazione locale è il motore di Windows PowerShell DSC (Desired State Configuration). Gestione configurazione locale viene eseguito in ogni nodo di destinazione ed è responsabile dell'analisi e dell'applicazione delle configurazioni inviate al nodo. È anche responsabile di alcuni altri aspetti di DSC, tra cui i seguenti.

* Determinazione della modalità di aggiornamento (push o pull).
* Definizione della frequenza in cui un nodo effettua il pull delle configurazioni e le applica.
* Associazione del nodo ai server di pull.
* Definizione di configurazioni parziali.

Per configurare Gestione configurazione locale in modo da specificare ognuno di questi comportamenti, è necessario usare un tipo speciale di configurazione. Le sezioni seguenti descrivono come configurare Gestione configurazione locale.

> **Nota**: questo argomento si applica alla versione di Gestione configurazione locale introdotta in Windows PowerShell 5.0. Per informazioni sulla configurazione di Gestione configurazione locale in Windows PowerShell 4.0, vedere [Gestione configurazione locale di Windows PowerShell 4.0 DSC (Desired State Configuration)](metaconfig4.md).

## Scrittura e applicazione di una configurazione di Gestione configurazione locale

Per configurare Gestione configurazione locale, è necessario creare ed eseguire un tipo speciale di configurazione. Per specificare una configurazione di Gestione configurazione locale, usare l'attributo DscLocalConfigurationManager. Di seguito viene mostrata una semplice configurazione che imposta Gestione configurazione locale in modalità push.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
} 
```

È necessario chiamare ed eseguire la configurazione per creare il file MOF di configurazione, proprio come per una configurazione normale. Per informazioni sulla creazione del file MOF di configurazione, vedere [Compilazione della configurazione](configurations.md#compiling-the-configuration). Diversamente dalle configurazioni normali, evitare di applicare una configurazione di Gestione configurazione locale chiamando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Chiamare invece il cmdlet [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), specificando il percorso del file MOF di configurazione come parametro. Dopo aver applicato la configurazione, è possibile visualizzare le proprietà di Gestione configurazione locale chiamando il cmdlet [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

Una configurazione di Gestione configurazione locale può contenere blocchi solo per un set limitato di risorse. Nell'esempio precedente l'unica risorsa chiamata è **Settings**. Le altre risorse disponibili sono le seguenti:

* **ConfigurationRepositoryWeb**: specifica un server di pull HTTP per le configurazioni. 
* **ConfigurationRepositoryShare**: specifica un server di pull SMB per le configurazioni.
* **ResourceRepositoryWeb**: specifica un server di pull HTTP per i moduli.
* **ResourceRepositoryShare**: specifica un server di pull SMB per i moduli.
* **ReportServerWeb**: specifica un server di pull HTTP a cui inviare i report.
* **PartialConfiguration**: specifica configurazioni parziali.

## Impostazioni di base

Oltre a specificare i server di pull e le configurazioni parziali, tutte le altre proprietà di Gestione configurazione locale vengono configurate in un blocco **Settings**. In un blocco **Settings** sono disponibili le proprietà seguenti.

|  Proprietà  |  Tipo  |  Descrizione   | 
|----------- |------- |--------------- | 
| ConfigurationModeFrequencyMins| UInt32| Frequenza, in minuti, in base alla quale la configurazione corrente viene controllata e applicata. Questa proprietà viene ignorata se la proprietà ConfigurationMode è impostata su ApplyOnly. Il valore predefinito è 15. __Nota__: il valore di questa proprietà deve essere un multiplo del valore della proprietà __RefreshFrequencyMins__ oppure il valore della proprietà __RefreshFrequencyMins__ deve essere un multiplo del valore di questa proprietà.| 
| RebootNodeIfNeeded| bool| Impostare questa proprietà su __$true__ per riavviare automaticamente il nodo dopo aver applicato una configurazione che richiede il riavvio. In caso contrario, sarà necessario riavviare manualmente il nodo per qualsiasi configurazione che lo richiede. Il valore predefinito è __$false__.| 
| ConfigurationMode| string | Specifica il modo in cui Gestione configurazione locale applica effettivamente la configurazione ai nodi di destinazione. Può accettare questi valori: __"ApplyOnly"__: DSC applica la configurazione e non esegue altre operazioni, a meno che non venga effettuato il push di una nuova configurazione nel nodo di destinazione o quando viene effettuato il pull di una nuova configurazione da un server. Dopo l'applicazione iniziale di una nuova configurazione, DSC non verifica l'eventuale desincronizzazione da uno stato configurato in precedenza. __"ApplyAndMonitor"__: questo è il valore predefinito. Gestione configurazione locale applica tutte le nuove configurazioni. Se dopo l'applicazione iniziale di una nuova configurazione il nodo di destinazione non è sincronizzato con lo stato desiderato, DSC segnala la discrepanza nei log. __"ApplyAndAutoCorrect"__: DSC applica tutte le nuove configurazioni. Se dopo l'applicazione iniziale di una nuova configurazione il nodo di destinazione non è sincronizzato con lo stato desiderato, DSC segnala la discrepanza nei log e quindi riapplica la configurazione corrente.| 
| ActionAfterReboot| string| Specifica che cosa avviene dopo un riavvio durante l'applicazione di una configurazione. I possibili valori sono: __"ContinueConfiguration"__: si continua ad applicare la configurazione corrente. __"StopConfiguration"__: la configurazione corrente viene arrestata.| 
| RefreshMode| string| Specifica il modo in cui Gestione configurazione locale ottiene le configurazioni. I possibili valori sono: __"Disabled"__: le configurazioni DSC sono disabilitate per questo nodo. __"Push"__: le configurazioni vengono avviate chiamando il cmdlet Start-DscConfiguration. La configurazione viene applicata immediatamente al nodo. Questo è il valore predefinito. __Pull__: il nodo è configurato per controllare regolarmente le configurazioni da un server di pull. Se questa proprietà è impostata su Pull, è necessario specificare un server di pull in un blocco __ConfigurationRepositoryWeb__ o __ConfigurationRepositoryShare__. Per altre informazioni sui server di pull, vedere [Configurazione di un server di pull DSC](pullServer.md).| 
| CertificateID| string| GUID che specifica un certificato usato per proteggere le credenziali per l'accesso alla configurazione. Per altre informazioni, vedere [Protezione delle credenziali in Windows PowerShell DSC (Desired State Configuration)](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).| 
| ConfigurationID| string| GUID che identifica il file di configurazione da ottenere da un server di pull in modalità pull. Nodo con configurazioni pull nel server di pull se il nome del file MOF di configurazione è ConfigurationID.mof. __Nota:__ se si imposta questa proprietà, la registrazione del nodo in un server di pull con __RegistryKeys__ non funziona. Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md).| 
| RefreshFrequencyMins| UInt32| Intervallo di tempo, in minuti, durante il quale Gestione configurazione locale controlla un server di pull per ottenere configurazioni aggiornate. Questo valore viene ignorato se Gestione configurazione locale non è configurato in modalità pull. Il valore predefinito è 30. __Nota__: il valore di questa proprietà deve essere un multiplo del valore della proprietà __ConfigurationModeFrequencyMins__ oppure il valore della proprietà __ConfigurationModeFrequencyMins__ deve essere un multiplo di questa proprietà.| 
| AllowModuleOverwrite| bool| __$TRUE__ se le nuove configurazioni scaricate dal server di configurazione possono sovrascrivere quelle meno recenti nel nodo di destinazione. In caso contrario, $FALSE.| 
| DebugMode| stringa| I possibili valori sono __None__ (predefinito), __ForceModuleImport__ e __All__. <ul><li>Impostare questa proprietà su __None__ per usare risorse memorizzate nella cache. Questa è l'impostazione predefinita e deve essere usata negli scenari di produzione.</li><li>L'impostazione __ForceModuleImport__ fa sì che Gestione configurazione locale ricarichi tutti i moduli di risorse DSC, anche se sono stati caricati e memorizzati nella cache in precedenza. Questa impostazione ha impatto sulle prestazioni delle operazioni di DSC, perché ogni modulo viene ricaricato al momento dell'uso. Questo valore viene in genere usato durante il debug di una risorsa.</li><li>In questa versione __All__ equivale a __ForceModuleImport__.</li></ul> |
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Usare blocchi __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ per definire i server di pull di configurazione.| 
| ResourceModuleManagers| CimInstance[]| Obsoleto. Usare blocchi __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ per definire i server di pull di risorse.| 
| ReportManagers| CimInstance[]| Obsoleto. Usare blocchi __ReportServerWeb__ per definire i server di pull di report.| 
| PartialConfigurations| CimInstance| Non implementata. Non utilizzare.| 
| StatusRetentionTimeInDays | UInt32| Numero di giorni per i quali Gestione configurazione locale mantiene lo stato della configurazione corrente.| 

## Server di pull

Un server di pull è una condivisione SMB o un servizio Web OData usato come posizione centrale per i file DSC. La configurazione di Gestione configurazione locale supporta la definizione dei tipi seguenti di server di pull:

* **Server di configurazione**: repository per le configurazioni DSC. Per definire i server di configurazione, usare blocchi **ConfigurationRepositoryWeb** (per server basati sul Web) e **ConfigurationRepositoryShare** (per server basati su SMB).
* Server di risorse: repository per risorse DSC, inclusi in pacchetti come moduli di PowerShell. Per definire i server di risorse, usare blocchi **ResourceRepositoryWeb** (per server basati sul Web) e **ResourceRepositoryShare** (per server basati su SMB).
* Server di report: servizio a cui DSC invia dati di report. Per definire i server di report, usare blocchi **ReportServerWeb**. Un server di report deve essere un servizio Web.

Per informazioni sulla configurazione e sull'uso di server di pull, vedere [Configurazione di un server di pull DSC](pullServer.md).

## Blocchi per i server di configurazione

Per definire un server di configurazione basato sul Web, creare un blocco **ConfigurationRepositoryWeb**. Un blocco **ConfigurationRepositoryWeb** definisce le proprietà seguenti.

|Proprietà|Tipo|Descrizione|
|---|---|---| 
|AllowUnsecureConnection|bool|Impostare questa proprietà su **$TRUE** per consentire le connessioni dal nodo al server senza autenticazione. Impostarla su **$FALSE** per richiedere l'autenticazione.|
|CertificateID|string|GUID che rappresenta il certificato usato per l'autenticazione nel server.|
|ConfigurationNames|String[]|Matrice di nomi di configurazioni di cui il nodo di destinazione deve effettuare il pull. Vengono usati solo se il nodo è registrato con il server di pull con **RegistrationKey**. Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md).|
|RegistrationKey|string|GUID che registra il nodo con il server di pull. Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md).|
|ServerURL|string|URL del server di configurazione.|

Per definire un server di configurazione basato su SMB, creare un blocco **ConfigurationRepositoryShare**. Un blocco **ConfigurationRepositoryShare** definisce le proprietà seguenti.

|Proprietà|Tipo|Descrizione|
|---|---|---|
|Credential|MSFT_Credential|Credenziale usata per l'autenticazione nella condivisione SMB.|
|SourcePath|string|Percorso della condivisione SMB.|

## Blocchi per i server di risorse

Per definire un server di risorse basato sul Web, creare un blocco **ResourceRepositoryWeb**. Un blocco **ResourceRepositoryWeb** definisce le proprietà seguenti.

|Proprietà|Tipo|Descrizione|
|---|---|---|
|AllowUnsecureConnection|bool|Impostare questa proprietà su **$TRUE** per consentire le connessioni dal nodo al server senza autenticazione. Impostarla su **$FALSE** per richiedere l'autenticazione.|
|CertificateID|string|GUID che rappresenta il certificato usato per l'autenticazione nel server.|
|RegistrationKey|string|GUID che identifica il nodo nel server di pull. Per altre informazioni, vedere la pagina su come registrare un nodo con un server di pull DSC.|
|ServerURL|string|URL del server di configurazione.|
 
Per definire un server di risorse basato su SMB, creare un blocco **ResourceRepositoryShare**. Un blocco **ResourceRepositoryShare** definisce le proprietà seguenti.

|Proprietà|Tipo|Descrizione|
|---|---|---|
|Credential|MSFT_Credential|Credenziale usata per l'autenticazione nella condivisione SMB.|
|SourcePath|string|Percorso della condivisione SMB.|

## Blocchi per i server di report

Un server di report deve essere un servizio Web OData. Per definire un server di report, creare un blocco **ReportServerWeb**. Un blocco **ReportServerWeb** definisce le proprietà seguenti.

|Proprietà|Tipo|Descrizione|
|---|---|---| 
|AllowUnsecureConnection|bool|Impostare questa proprietà su **$TRUE** per consentire le connessioni dal nodo al server senza autenticazione. Impostarla su **$FALSE** per richiedere l'autenticazione.|
|CertificateID|string|GUID che rappresenta il certificato usato per l'autenticazione nel server.|
|RegistrationKey|string|GUID che identifica il nodo nel server di pull. Per altre informazioni, vedere la pagina su come registrare un nodo con un server di pull DSC.|
|ServerURL|string|URL del server di configurazione.|

## Configurazioni parziali

Per definire una configurazione parziale, creare un blocco **PartialConfiguration**. Per altre informazioni sulle configurazioni parziali, vedere [Configurazioni parziali DSC](partialConfigs.md). Un blocco **PartialConfiguration** definisce le proprietà seguenti.

|Proprietà|Tipo|Descrizione|
|---|---|---| 
|ConfigurationSource|string[]|Matrice di nomi di server di configurazione, definiti in precedenza in blocchi **ConfiguratoinRepositoryWeb** e **ConfigurationRepositoryShare**, da cui viene effettuato il pull della configurazione parziale.|
|DependsOn|string{}|Elenco di nomi di altre configurazioni che devono essere completate prima di poter applicare questa configurazione parziale.|
|Description|string|Testo usato per descrivere la configurazione parziale.|
|ExclusiveResources|string[]|Matrice di risorse esclusive per questa configurazione parziale.|
|RefreshMode|string|Specifica il modo in cui DSC ottiene la configurazione parziale. I possibili valori sono: **Disabled**: la configurazione parziale è disabilitata. **Push**: viene effettuato il push della configurazione parziale nel nodo chiamando il cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx). Dopo il push o il pull di tutte le configurazioni parziali per il nodo da un server, la configurazione può essere avviata chiamando `Start-DscConfiguration –UseExisting`. Questo è il valore predefinito. **Pull**: il nodo è configurato per controllare regolarmente la configurazione parziale da un server di pull. Se questa proprietà è impostata su "Pull", è necessario specificare un server di pull impostando la proprietà **ConfigurationSource**. Per altre informazioni sui server di pull, vedere [Configurazione di un server di pull DSC](pullServer.md).|
|ResourceModuleSource|string[]|Matrice di nomi dei server di risorse da cui scaricare le risorse necessarie per questa configurazione parziale. Questi nomi devono fare riferimento ai server di risorse definiti in precedenza in blocchi **ResourceRepositoryWeb** e **ResourceRepositoryShare**.|

## Vedere anche 

### Concetti
[Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md)
 
[Configurazione di un server di pull DSC](pullServer.md) 

[Gestione configurazione locale di Windows PowerShell 4.0 DSC (Desired State Configuration)](metaConfig4.md) 

### Risorse aggiuntive
[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 

[Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md) 



<!--HONumber=Jun16_HO1-->


