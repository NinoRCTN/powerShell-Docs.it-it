# Rappresentazione degli stati unificata e coerente

In questa versione è stata introdotta una serie di miglioramenti per lo stato di Gestione configurazione locale e lo stato di DSC generati dall'automazione. I miglioramenti includono rappresentazioni dello stato unificate e coerenti, una proprietà datetime gestibile per gli oggetti di stato restituiti dal cmdlet Get-DscConfigurationStatus e una proprietà con dettagli avanzati sullo stato di Gestione configurazione locale restituita dal cmdlet Get-DscLocalConfigurationManager.

La rappresentazione dello stato di Gestione configurazione locale e delle operazioni DSC è stata rivista e unificata in base alle regole seguenti:
1.  La risorsa non elaborata non influisce sullo stato di Gestione configurazione locale e DSC.
2.  Gestione configurazione locale interrompe l'elaborazione di ulteriori risorse quando rileva una risorsa che richiede il riavvio.
3.  Una risorsa che richiede il riavvio non è nello stato desiderato fino all'effettiva esecuzione del riavvio.
4.  In presenza di una risorsa in errore, Gestione configurazione locale continua con l'elaborazione di altre risorse, a condizione che non siano dipendenti da quelle in errore.
5.  Lo stato complessivo restituito dal cmdlet Get-DscConfigurationStatus è il soprainsieme dello stato di tutte le risorse.
6.  Lo stato PendingReboot è un soprainsieme dello stato PendingConfiguration.

Nella tabella seguente sono illustrate le proprietà correlate allo stato risultanti in alcuni scenari tipici.

| **Scenario**                    | **LCMState\***       | **Stato** | **RebootRequested**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Idle                 | Operazione completata    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Operazioni non riuscite    | $false        | $null                        | F                              |
| S,F                             | PendingConfiguration | Operazioni non riuscite    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | Operazioni non riuscite    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Operazioni non riuscite    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Operazioni non riuscite    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Operazione completata    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Operazioni non riuscite    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Operazione completata    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Operazione completata    | $true         | $null                        | r                              |

^
S<sub>i</sub>: una serie di risorse applicata correttamente F<sub>i</sub>: una serie di risorse applicata non correttamente r: una risorsa che richiede il riavvio
\*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## Miglioramenti per il cmdlet Get-DscConfigurationStatus

In questa versione sono stati introdotti alcuni miglioramenti per il cmdlet Get-DscConfigurationStatus. In precedenza, la proprietà StartDate degli oggetti restituiti dal cmdlet è di tipo String. Ora è di tipo Datetime e questo facilita operazioni complesse di selezione e filtro basate sulle proprietà intrinseche di un oggetto Datetime.
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Ecco un esempio che restituisce tutti i record di operazioni DSC eseguite nello stesso giorno della settimana di oggi.
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Vengono eliminati i record delle operazioni che non apportano modifiche alla configurazione del nodo, ad esempio le operazioni di sola lettura. Pertanto, le operazioni Test-DscConfiguration e Get-DscConfiguration non vengono più modificate negli oggetti restituiti dal cmdlet Get-DscConfigurationStatus.
I record dell'operazione di impostazione della metaconfigurazione viene aggiunto all'oggetto restituito dal cmdlet Get-DscConfigurationStatus.

Di seguito è riportato un esempio di risultato restituito dal cmdlet Get-DscConfigurationStatus -All.
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## Miglioramenti per il cmdlet Get-DscLocalConfigurationManager
È stato aggiunto un nuovo campo LCMStateDetail all'oggetto restituito dal cmdlet Get-DscLocalConfigurationManager. Questo campo viene popolato quando LCMState è "Busy". Può essere recuperato dal cmdlet seguente:
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Quello che segue è un esempio dell'output di un'operazione di monitoraggio continuo per una configurazione che richiede due riavvii in un nodo remoto.
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```


<!--HONumber=Jun16_HO4-->


