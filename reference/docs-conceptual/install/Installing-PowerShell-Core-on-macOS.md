---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: ad1306e99261e8e6e2fd49d3199d863929c31e92
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444432"
---
# <a name="installing-powershell-core-on-macos"></a>Installazione di PowerShell Core in macOS

PowerShell Core supporta macOS 10.12 e versioni successive.
Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.
Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.

> [!TIP]
> Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="about-brew"></a>Informazioni su Brew

[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.
Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni specifiche][brew].
In alternativa, è possibile installare PowerShell tramite [download diretto](#installation-via-direct-download) o da [archivi di file binari](#binary-archives).

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva

Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.

A questo punto, è possibile installare PowerShell:

```sh
brew cask install powershell
```

Infine, verificare che l'installazione funzioni correttamente:

```sh
pwsh
```

Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire da PowerShell e riavviare la shell per completare l'aggiornamento e aggiornare i valori visualizzati in `$PSVersionTable`.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva

Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.

Dopo aver installato Homebrew, è possibile installare PowerShell.
Per prima cosa installare il pacchetto [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:

```sh
brew tap homebrew/cask-versions
```

A questo punto, è possibile installare PowerShell:

```sh
brew cask install powershell-preview
```

Infine, verificare che l'installazione funzioni correttamente:

```sh
pwsh-preview
```

Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento
> e aggiornare i valori visualizzati in `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installazione tramite download diretto

Scaricare il pacchetto PKG `powershell-6.2.0-osx-x64.pkg`
dalla pagina delle [versioni][] nel computer macOS.

È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Installare [OpenSSL](#install-openssl). OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.

## <a name="binary-archives"></a>Archivi di file binari

Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.

### <a name="installing-binary-archives-on-macos"></a>Installazione degli archivi binari in macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

Installare [OpenSSL](#install-openssl). OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.

## <a name="installing-dependencies"></a>Installazione delle dipendenze

### <a name="install-xcode-command-line-tools"></a>Installare gli strumenti della riga di comando XCode

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Installare OpenSSL

OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM. È possibile eseguire l'installazione tramite MacPorts o Brew.

#### <a name="install-openssl-via-brew"></a>Installare OpenSSL tramite Brew

Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.

Per installare OpenSSL, eseguire `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>Installare OpenSSL tramite MacPorts

1. Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools).
1. Installare MacPorts.
   Se sono necessarie istruzioni, vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html).
1. Aggiornare MacPorts eseguendo `sudo port selfupdate`.
1. Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`.
1. Installare OpenSSL eseguendo `sudo port install openssl`.
1. Collegare le librerie per renderle disponibili per PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Disinstallazione di PowerShell Core

Se PowerShell è stato installato con Homebrew, usare il comando seguente per la disinstallazione:

```sh
brew cask uninstall powershell
```

Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.

> [!NOTE]
> Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.

## <a name="paths"></a>Percorsi

* `$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/`
* I profili utente vengono letti da `~/.config/powershell/profile.ps1`
* I profili predefiniti vengono letti da `$PSHOME/profile.ps1`
* I moduli utente vengono letti da `~/.local/share/powershell/Modules`
* I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`
* I moduli predefiniti vengono letti da `$PSHOME/Modules`
* La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

I profili rispettano la configurazione di PowerShell per ogni host.
Di conseguenza, il profilo specifico dell'host predefinito è presente in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.

PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.

Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.
Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Risorse aggiuntive

* [Sito Web di Homebrew][brew]
* [Repository Github di Homebrew][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
