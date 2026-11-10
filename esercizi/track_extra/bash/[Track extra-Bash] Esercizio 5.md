**ODD/EVEN:** Scrivere uno script che accetti un argomento numerico e stampi la sequenze di numeri da 1 a quel numero con l'indicazione se è pari o dispari. Controllare il corretto numero di argomenti passati allo script e che l'argomento sia di tipo numerico, in caso contrario generare una condizione di errore.

Prima versione, con input da parte dell'utente:
```bash
read -p "Inserisci valore: " valore #riga che prende l'input
while true; do
	if let $valore 2>/dev/null; then #con let controllo che il valore sia numerico
		break
	else
		echo "Error: il valore inserito non è un numero"
		read -p "Inserisci valore: " valore
	fi
done

for ((i=1; i<$valore+1; i++)); do
	if ((i%2==0)); then
		echo "$i: pari"
	else
		echo "$i: dispari"
	fi
done
```

Versione a parametro:
```bash
if ! let $1 2>/dev/null; then
	echo "Error: il valore inserito non è un numero"
fi

for ((i=1; i<$1+1; i++)); do
	if ((i%2==0)); then
		echo "$i: pari"
else
	echo "$i: dispari"
fi
done
```