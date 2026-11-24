**IPV4 REGEX**: Scrivere una o più espressioni regolari (in OR) che matchino tutti i possibili indirizzi ipv4 in decimal dottet notation.

Soluzione:
```
^((0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])$
```

Soluzione alternativa:
```sh
(?<![\w\d.])((0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])(?![\w\d.])
```

Spiegazione:
- `0` caso solo 0
- `1[0-9]{2}` caso da 100 a 199
- `[1-9][0-9]?` caso da 1 a 99
- `2[0-4][0-9]` caso da 200 a 249
- `25[0-5]` caso da 250 a 255

Con la soluzione 1 limito a inizio e fine riga, quindi solo un ip nella riga.
Con la soluzione 2 posso cercarla all'interno dei testi utilizzando i costrutti speciali:
- `(?<![\w\d.])` per dire che prima della ricerca non devono esserci parole, numeri o il '.' attaccato
- `(?![\w\d.])` simile all'inizio, ma per la fine