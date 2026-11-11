- **AWK:** Scrivere un programma AWK che prende in input un file .csv e stampa il terzo campo solo se viene matchata la stringa "banana".

File di input di esempio:

    apple,banana,strawberry  
    pear,peach,lemon  
	banana,kiwi,orange

Output desiderato:

    strawberry  
    orange

Soluzione:
```shell
#!/usr/bin/env bash
if [[ $# -ne 1 ]]; then
	echo "Parametri ricevuti: '$#', fornire un solo file"
	exit 1
fi

if [[ -f "$1" && "$1" == *.csv ]]; then
	awk -F ',' '/banana/ { print $3 }' "$1"
else
	echo "File '$1' non esistente o formato non .csv"
	exit 2
fi
```