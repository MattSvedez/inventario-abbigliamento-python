# Inventario di abbigliamento in Python

Un piccolo sistema che ho scritto per gestire l'inventario di un negozio di abbigliamento: registra i capi, li mostra, li cerca con filtri combinabili e ne calcola alcune statistiche

## Perché l'ho fatto

È il mio primo progetto in Python, svolto durante il Master in Data Science, Analytics e Agenti AI di start2impact

Volevo mettere insieme liste, tuple, dizionari, funzioni, condizioni e cicli in un caso concreto, e muovere i miei primi passi con il linguaggio

## Cosa fa

Il codice è diviso in quattro funzioni, una per ogni operazione

`registra_elemento` ripulisce i dati (spazi e maiuscole), controlla che la condizione sia nuovo, ottimo, buono o usato, rifiuta i prezzi negativi ed evita i doppioni, poi assegna al capo un ID progressivo

`visualizza_elementi` stampa un capo per riga e avvisa se l'inventario è vuoto

`ricerca_elementi` accetta quattro filtri opzionali, cioè tipo, condizione, colore e prezzo, che si possono usare da soli o insieme

`statistiche` mostra il totale dei capi, la distribuzione per condizione, il tipo più frequente e il capo registrato per ultimo

## Anteprima

Dopo aver registrato una giacca nera e un maglione blu, `statistiche(inventario)` stampa:

```text
Totale capi: 2

Distribuzione per condizione:
- nuovo : 1
- ottimo : 1

Tipo più frequente: giacca ( 1 )

Capo più recente:
ID: 2 | Tipo: maglione | Colore: blu | Taglia: L | Prezzo: 29.9 € | Condizione: ottimo
```

## Come eseguirlo

Servono Python 3 e Jupyter Notebook, poi basta clonare il repository e aprire il notebook:

```bash
git clone https://github.com/MattSvedez/inventario-abbigliamento-python.git
cd inventario-abbigliamento-python
pip install notebook
jupyter notebook notebooks/sistema-gestione-inventario.ipynb
```

Le celle si eseguono dall'alto in basso

## Esempio di utilizzo

Così si registra un capo e poi lo si cerca nell'inventario:

```python
inventario = []
id_progressivo = 1
condizioni_ammesse = ["nuovo", "ottimo", "buono", "usato"]

inventario, id_progressivo, _ = registra_elemento(
    inventario, id_progressivo,
    tipo="Giacca", colore="Nero", taglia="M",
    prezzo=19.99, condizione="Nuovo",
    condizioni_ammese=condizioni_ammesse
)

visualizza_elementi(inventario)
# Elenco capi in inventario:
# ID: 1 | Tipo: giacca | Colore: nero | Taglia: M | Prezzo: 19.99 € | Condizione: nuovo

risultati = ricerca_elementi(inventario, tipo="giacca", condizione="nuovo")
visualizza_elementi(risultati)
```

Se i dati non sono validi la funzione si ferma con un `ValueError` che ne spiega il motivo, per esempio «Il prezzo non può essere negativo» oppure «Capo duplicato: esiste già»

## Struttura del progetto

```text
inventario-abbigliamento-python/
|-- README.md
|-- LICENSE
|-- .gitignore
|-- notebooks/
|   |-- sistema-gestione-inventario.ipynb   codice, esempi e output
```

## Cosa ho imparato

In questo progetto ho capito come un capo diventi un dizionario, l'inventario una lista di dizionari e il risultato di una funzione una tupla, e che controllare i dati prima di salvarli evita errori più avanti

Ho imparato anche a rendere opzionali i filtri con il valore predefinito `None`, così la stessa funzione di ricerca serve in più modi, e a contare e trovare il massimo con `dict.get()`, `max()` e una `lambda`

## Prossimi passi

Mi piacerebbe far inserire i capi dall'utente con `input()`, salvare e rileggere l'inventario da un file e segnalare un pari merito quando due tipi sono ugualmente frequenti

## Contributo di Claude

Il progetto, il codice e le idee sono interamente miei: Claude, l'assistente di Anthropic, mi ha aiutato soltanto a caricarlo su GitHub e a preparare il repository, cioè README, licenza e `.gitignore`

## Licenza

MIT, vedi il file [LICENSE](LICENSE)
