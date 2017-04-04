# <a name="style-guide-for-powershell-docs"></a>Guida di stile per la documentazione di PowerShell


## <a name="titlesheadings"></a>Titoli/intestazioni

* I titoli e le intestazioni (qualsiasi elemento preceduto da \#) devono essere seguiti da una nuova riga
* Solo la prima lettera di un titolo e gli eventuali nomi propri nel titolo devono essere in maiuscolo
* Ogni documento deve includere un solo titolo H1
* In caso di modifica di contenuto di riferimento, i titoli H2 sono richiesti da platyPS e non devono essere aggiunti o rimossi perché ciò causerà un errore di compilazione
* Usare solo intestazioni con lo stile \#, invece di intestazioni con = o \-

### <a name="correct"></a>Corretto

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a>Non corretto

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a>Sintassi

* Nelle citazioni di un cmdlet in un paragrafo usare \` per evidenziare i nomi dei cmdlet
  * Durante la scrittura di un articolo (diversamente dal contenuto di riferimento), la prima istanza del nome di un cmdlet deve essere un collegamento alla documentazione del cmdlet
* In tutti i blocchi di sintassi di PowerShell è necessario usare &#96;&#96;&#96;powershell
* Non iniziare i comandi di PowerShell con "C:\PS> "
* L'output generato dai comandi di PowerShell deve essere impostato come commento per evitare l'applicazione dell'evidenziazione della sintassi
* I nomi di proprietà e parametri devono essere in **grassetto**


## <a name="lists"></a>Elenchi

* Non terminare gli elementi di elenco con un punto (a meno che non contengano più frasi)
* Se l'elenco contiene più frasi, valutare la possibilità di usare un'intestazione 3/4/5 (se applicabile) dopo il concetto principale

## <a name="links"></a>Collegamenti

* I collegamenti devono essere sempre contrassegnati con la sintassi di Markdown `[friendlyname](url)`
* I collegamenti devono avere un nome descrittivo quando possibile, molto probabilmente il titolo della pagina collegata
  * **Eccezione**: i collegamenti che indirizzano a siti non Microsoft devono contenere solo un URL
* Tutti gli elementi nella sezione "Collegamenti correlati" in fondo all'articolo devono essere impostati come collegamenti ipertestuali. 

## <a name="line-breaks"></a>Interruzioni di riga

* È necessario includere interruzioni di riga semantiche
* Le righe devono essere limitate a 100 caratteri (elemento aperto: strumento per verificare questo aspetto)
* È POSSIBILE rimuovere le interruzioni di riga aggiuntive per PS4 +, ma NON per PS3 (convalida richiesta)