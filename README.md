# Multiselect-Dropdown

- Versione:1.0.1
- Originale: https://admirhodzic.github.io/
- Versione JQ: Casalegno Marco https://github.com/casalegno/multiselect-dropdown

Esistono due versioni di questo script. Una in pure JS ed una per Jquery
Quella per JS non richiede nessuna dipendenza, crea un dropdown con dei checkbox per la selezione multipla.
Quello per Jquery fa la medesima cosa ma viene chiamato da Jquery indicando quale elemento deve essere chiamato.
Pure JavaScript, no dependencies, dropdown list with multiselect capability.
## Installazione
#### Versione standard
L'installazione prevede semplicemente la chiamata allo script.
``` html
<script src="multiselect-dropdown.js" ></script>
```
#### Versione Jquery
Nella versione per Jquery è necessario la chiamata a Jquery.
``` html
<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
<script src="multiselect-dropdown-jq.js" ></script>
```
In entrambi i casi è necessario includere il foglio css per la visualizzazione del dropdown
## Utilizzo del plugin
#### Versione standard
Per far funzionare il multiselect su tutta la pagina è sufficiente assegnare l'attributo multiple ai select che vogliare renderizzare.
``` html
<select multiple id="sel1"> 
... 
</select>
```
#### Versione Jquery
Nella versione con Jquery, non dobbiamo preoccuparci di modificare il contenuto dell'html. Penserà lo script a farlo.
Pero dobbiamo attivare il plugin con uno script JS
``` js
$('select').msdd(); //renderizza tutti i select
$('#selectID').msdd(); //renderizza solo quello selezionato
```
## Attributi aggiuntivi
Per abilitare gli attributi aggiuntivi, dobbiamo semplicemente inserire i relativi attributi nel corpo html del select, con valore true
```html
<select multiple 
    multiselect-search="true" 
    multiselect-select-all="true" 
    multiselect-max-items="3"
    multiselect-hide-x = "false"
    >
    ... 
</select>
```
##### multiselect-select-all="true":
Permette di inserire una opzione per selezionare tutti i campi.
Default: false;
##### multiselect-max-items="3"
L'attributo permette di selezionare un numero massimo di oggetti visualizzati nel select chiuso. Default: 10
##### multiselect-hide-x="true"
Questo attributo rimuove il pulsante di cancellazione dell'opzione selezionata nel select chiuso. 
Default: false;
##### multiselect-search="true" 
Questo attributo permette di attivare un campo di filtraggio per le opzioni

### JavaScript API
Per estendere la lista delle opzioni si puo utilizzare la funzione di caricamento opzioni sull'id del select.
```
fetch("/options").then(d=>d.json()).then(d=>{
      sel1.innerHTML = 
        d.map(t=>'<option value="'+t.value+'">'+t.text+'</option>');

      sel1.loadOptions();
    })
```
