**Esercizio 2**
- **Numero Processi:** Contare il numero totale di processi attualmente in esecuzione sulla propria macchina senza utilizzare utility interattive come "top".
Soluzione:
ps restituisce una lista statica dei processi attivi, non interattiva come top, e solo quelli attivi nel terminale attuale. Con **-e** o **-A** seleziono tutti i processi e con la pipe li passo a word count **wc**
```bash
ps -e | wc -l
```
Output:
```bash
[viron@localhost ~]$ ps -e | wc -l
117
```

