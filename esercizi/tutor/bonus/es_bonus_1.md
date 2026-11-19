Supponiamo abbiamo file `.csv` separato in colonne da una `,` (virgola)
Riempito con le generalità delle persone: `nome,cognome,numero,residenza`
Utilizzando solamente i comandi `grep, sed, awk`:
- estrarre solo una colonna (cognomi)
- dalla colonna fare in modo che la prima lettera diventi maiuscola
- selezionare due cognomi

File input:
```sh
$ cat es_bonus_1.csv 
viron,daiu,1234567890,roma
mario,rossi,2348024831,roma
giorgio,bianchi,1047238965,milano
alessio,neri,7584937564,genova
mattia,verdi,5638294759,bari
```

Soluzione: (Supposto che il file sia corretto)
Utilizzo `awk` per separare tramite `,` e prendere solo la colonna dei cognomi.
Passo il risultato a `sed` che sostituisce il primo carattere (preso tramite la regex `.`) con l'uppercase dell'occorrenza presa nella regex
Perché solo `.`? Perché la richiesta chiede solo la prima lettera e con il `.` finisco per prendere sempre il primo carattere del cognome (avendolo filtrato in precedenza con `awk`). Si poteva prendere anche con `[a-zA-Z]`.
Infine, con `grep` prendo due cognomi a scelta.

Una prima soluzione trovata:
```sh
awk -F, '{print $2}' es_extra_1.csv | sed -E 's/./\U&/' | egrep -i "daiu|neri"
```

Versione più efficiente: (supponendo che i caratteri siano tutti minuscoli, altrimenti a `grep` va aggiunto `-i`)
Cambiando l'ordine di `grep` e `sed` non faccio la sostituzione di tutte le righe dei cognomi come facevo sopra, ma solo di quelle filtrate.
```sh
awk -F, '{print $2}' es_extra_1.csv | egrep "daiu|neri" | sed -E 's/./\U&/'
```

Output:
```sh
Daiu
Neri
```