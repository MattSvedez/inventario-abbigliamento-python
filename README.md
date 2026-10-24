# Inventario di abbigliamento in Python

Un piccolo sistema per gestire l'inventario di un negozio di abbigliamento: registra i capi, li mostra, li cerca con filtri combinabili e ne calcola alcune statistiche.

## Perché l'ho fatto

È il mio primo progetto in Python, svolto durante il Master in Data Science, Analytics e Agenti AI di start2impact. Lo scopo era mettere insieme liste, tuple, dizionari, funzioni, condizioni e cicli in un caso concreto, e imparare a muovere i primi passi con il linguaggio.

## Funzionalità

- **Registrare** un capo (`registra_elemento`): ripulisce i dati (spazi e maiuscole), verifica che la condizione sia tra nuovo, ottimo, buono e usato, rifiuta i prezzi negativi ed evita i doppioni. Ogni capo riceve un ID progressivo.
- **Visualizzare** l'inventario (`visualizza_elementi`): stampa un capo per riga, oppure avvisa se l'inventario è vuoto.
- **Cercare** (`ricerca_elementi`): quattro filtri opzionali, cioè tipo, condizione, colore e prezzo, che si usano da soli o insieme.
- **Analizzare** (`statistiche`): totale dei capi, distribuzione per condizione, tipo più frequente e capo più recente.

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

Serve Python 3 e Jupyter Notebook.

```bash
git clone https://github.com/MattSvedez/inventario-abbigliamento-python.git
cd inventario-abbigliamento-python
pip install notebook
jupyter notebook notebooks/sistema-gestione-inventario.ipynb
```

Poi si eseguono le celle dall'alto in basso.

## Esempio di utilizzo

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

Se i dati non sono validi, la funzione si ferma con un `ValueError` che spiega il motivo, per esempio «Il prezzo non può essere negativo.» oppure «Capo duplicato: esiste già».

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

- Un dato può essere rappresentato come dizionario (un capo), raccolto in una lista (l'inventario) e restituito da una funzione come tupla.
- Controllare i dati prima di salvarli evita errori più avanti.
- Filtri opzionali con valore predefinito `None` permettono di usare la stessa funzione di ricerca in modi diversi.
- Conteggi con `dict.get()` e ricerca del massimo con `max()` e una `lambda`.

## Prossimi passi

- Far inserire i capi dall'utente con `input()`.
- Salvare e rileggere l'inventario da un file.
- Segnalare un pari merito quando due tipi sono ugualmente frequenti.

## Contributo di Claude

Il progetto, il codice e le idee sono interamente miei. Claude, l'assistente di Anthropic, mi ha aiutato soltanto a caricare il progetto su GitHub e a preparare il repository (README, licenza e `.gitignore`).

## Licenza

MIT. Vedi il file [LICENSE](LICENSE).
