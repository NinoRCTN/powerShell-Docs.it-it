# Risorse DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC. Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.

Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.  I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.  

Le risorse DSC vengono descritte negli argomenti seguenti:

- [Risorse DSC predefinite](builtInResource.md)
- [Creare risorse DSC personalizzate](authoringResource.md)
- [Risorse DSC predefinite per Linux](lnxBuiltInResources.md)<!--HONumber=Feb16_HO4-->
