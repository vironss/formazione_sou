**Esercizio 3**
- **Kernel Version:** Trovare il modo (o più modi) per capire se il Kernel attualmente running è il più recente installato sulla macchina. Scrivere uno script che esegua automaticamente il controllo e risponda TRUE/FALSE.
Soluzione:
Prendo la versione del kernel attualmente in uso

Con
```bash
rpm -q kernel
```
prendo tutti i kernel installati, li ordino in base alla versione, prendo solo l'ultima e infine lo pulisco.

Con un if effettuo un confronto tra le due versioni e restituisco TRUE se sono della stessa versione. Infine ho una stampa finale per il controllo

```bash 
#! /bin/bash
current=$(uname -r)
latest=$(rpm -q kernel|sort -V|tail -n 1|awk -F'l-' '{print $2}')

if [[ "$current" == "$latest" ]];then
echo "TRUE"
else
echo "FALSE"
fi
echo "current: $current" && echo "latest: $latest"
```
Output:
```bash
TRUE
current: 5.14.0-687.64.1.el9_8.x86_64
latest: 5.14.0-687.64.1.el9_8.x86_64
```
