# Forms HTML Struttura e Sintassi

I form nel linguaggio HTML sono elementi fondamentali per la raccolta degli input dei frequentatori dei tuoi siti.
Mailing list, form di contatto, e commenti ai post sono esempi comuni per piccoli siti, mentre per le grandi aziende sono l'elemento cardine nella gestione degli E-commerce.

Un form ben scritto e strutturato può rappresentare una sensibile differenza nella promozione di una campagna aziendale, o del suo business in generale, per questo il form, è uno degli elementi su cui viene posta la maggior attenzione in fase di studio, nella creazione di un sito.

Iniziamo a vedere gli elementi di base che compongono un form:
```
<form action='#' method='get' class='our-first-form'>
</form>
```
**Action** è l'attributo che definisce l'url a cui viene inviato l'input nel momento in cui l'utente invia il form, è un url particolare definito dal server. (Per ora possiamo ignorarlo)

**Method** è un attributo che può assumere i valori **post** o **get**, entrambi definiscono il modo in cui il form è inviato al server. In linea generale si utilizza **post** esclusivamente quando andiamo a cambiare i dati sul server e **get** quando ci limitiamo a prenderli in prestito. (Per ora possiamo ignorare anche questo evitando proprio di usare l'attributo nel tag, bella la vita eh?)

**Class** a questo punto della storia possiamo dire che si spiega da sè.

Procediamo dunque analizzando i campi che possiamo inserire nel nostro form;
Il primo elemento e di certo il più utilizzato, è il campo di digitazione testuale, il quale a seconda delle necessità può ricoprire svariati ruoli, ad esempio;
- Dati anagrafici
- Email
- Numeri di carta di credito

Ogni campo è accompagnato da una label che ne definisce lo scopo, alternativamente, ma non altrettanto efficace, si può utilizzare un placeholder al suo interno, ossia una riga di testo che descrive il campo, il cui compito è sparire quando il campo è selezionato.

>Il problema nell'utilizzo dei placeholder al posto delle etichette consiste nel fatto che provoca nell'utente uno stress mentale superfluo, in quanto lo porterà a chiedersi se quel testo sparirà da solo, o se dovrà cancellarlo manualmente una volta selezionato il campo, e anche se si tratta di valutazioni effettivamente molto rapide è un qualcosa che peggiora l'esperienza dell'utente, complicandola.

Per definire un campo di testo dunque inseriamo prima la sua label e poi il campo effettivo:

```
<form action='#'>
<label for="form-username"> Nome utente </label>
<input type="text" id="username" name="form-username" required>
</form>
```

**for=""** specifica a quale elemento la label fa riferimento, il quale viene espresso come **id** nel tag input, come best practice convinene sempre iniziare con la parola form, per contraddistinguerlo dagli id del resto di pagina e renderlo facilmente individuabile.

**type=""** definisce il tipo di input che andremo a ricevere, i più comuni sono text, tel, email, ma ce ne sono molti altri per personalizzare al massimo il nostro form.

**name=""** l'input da noi ricevuto rappresenta una variabile a livello di server, questo attributo specifica il nome della suddetta.

**required** effettua una pre-validazione del form a livello del browser invece che del server. Specificando infatti **required** in un campo, il form non potrà essere inviato dall'utente a meno che quel campo non sia collegato.

**pattern=""** per effettuare un'ulteriore pre-validazione sui dati inseriti, possiamo specificare un pattern che l'input deve rispettare per essere considerato valido, ad esempio:
```
<input type="text" id="username" name="username" pattern="[A-Z a-z] {3,}">
```
il pattern sopra specificato ci dice che, i caratteri considerati validi in quell'input sono solo le lettere ([A-Z a-z] quindi sia maiuscole che minuscole) e che la lunghezza di quell'input deve essere dai 3 caratteri in su ({3,}), mentre specificando solo un numero, ad esempio {3}, imponiamo un numero fisso di caratteri, oppure possiamo impostarne un range specificando 2 valori {3,20}.

Per l'inserimento di un input di testo più consistente (come ad esempio i commenti degli utenti in un blog) utilizzeremo invece **Textarea**

```
<label for="form-comment">Indicazioni aggiuntive:</label>
    <textarea name="comment" id="form-comment"></textarea> 
```

Attenzione, **textarea** non è autochiudente come il tag input!

Un altro elemento molto utile per esprimere delle scelte in un range predefinito di opzioni è il **Radio Button** il quale permette una singola scelta in una lista di possibilità.

Per strutturare una lista di scelte dipendente dai radio buttons andremo a racchiuderla interamente in un **fieldset** etichettandola con **legend** invece che con un semplice **label**, il quale invece servirà per etichettare le opzioni disponibili:
```
<fieldset>
    <legend> Menù Pizze </legend>
    <input type="radio" id="opzione1" name="opzione-input" value="margherita" checked>
    <label for="opzione1"> Margherita </label>
    <input type="radio" id="opzione2" name="opzione-input" value="quattro-formaggi">
    <label for="opzione2"> Quattro Formaggi </label>
    <input type="radio" id="opzione3" name="opzione-input" value="speck-provola">
    <label for="opzione3"> Speck e Provola </label>
</fieldset>
```
In questo caso, per assegnare un valore di default alla scelta, o comunque costringere l'utente a fare una scelta all'interno della stessa, possiamo specificare alla fine del tag input l'attributo **checked** in maniera che al momento del caricamento della pagina quell'opzione sia già contrassegnata.

Alternativamente ai radio button, per effettuare una singola scelta da una lista di opzioni, possiamo usare **select** per creare il classico menù a tendina:

```
<label for="menu"> Seleziona pizza </label>
<select id="pizza" name="gusto">
<option value="margherita"> Margherita </option>
<option value="quattro-formaggi"> Quattro Formaggi </option>
<option value="speck-provola"> Speck e Provola </option>
</select>
```

Nel caso vi sia la necessità di scegliere più opzioni dalla lista (o semplicemente dare all'utente la possibilità di selezionare e deselezionare un determinato campo) possiamo avvalerci dei checkbox:
```
<legend> Aggiungi ingredienti </legend>
<label class='checkbox-label' for='funghi'>
  <input id='funghi' name='add-on' type='checkbox' value='funghi'/>
    Funghi + 1,00€</label>
<label class='checkbox-label' for='salamep'>
  <input id='salamep' name='add-on' type='checkbox' value='salame-piccante'/>
    Salame piccante + 1,00€</label>
<label class='checkbox-label' for='mozzarella'>
  <input id='mozzarella' name='add-on' type='checkbox' value='doppia-mozzarella'/>
    Doppia mozzarella + 1,00€</label>
```
a differenza dei radio button, i checkbox non necessitano di essere racchiusi in un **fieldset** (che ho aggiunto nel codice allegato solo per una questione di stile), ma nel loro utilizzo è una best practice svilupparli interamente all'interno della loro label.