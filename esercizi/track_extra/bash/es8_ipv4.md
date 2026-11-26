**IPV4 REGEX**: Scrivere una o più espressioni regolari (in OR) che matchino tutti i possibili indirizzi ipv4 in decimal dottet notation.

Soluzione:
```
\b((0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])\b
```

Spiegazione:
- `0` caso solo 0
- `1[0-9]{2}` caso da 100 a 199
- `[1-9][0-9]?` caso da 1 a 99
- `2[0-4][0-9]` caso da 200 a 249
- `25[0-5]` caso da 250 a 255

