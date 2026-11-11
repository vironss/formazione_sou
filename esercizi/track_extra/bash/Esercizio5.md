**ODD/EVEN:** Scrivere uno script che accetti un argomento numerico e stampi la sequenze di numeri da 1 a quel numero con l'indicazione se è pari o dispari. Controllare il corretto numero di argomenti passati allo script e che l'argomento sia di tipo numerico, in caso contrario generare una condizione di errore.

Soluzione:
```bash
if [[ $# > 1 ]]; then
	echo "Accetta un solo parametro"
	exit 1
elif [[ $1 =~ ^[0-9]*$ ]]; then
	for ((i=1; i<$1+1; i++)); do
		if ((i%2==0)); then
			echo "$i:pari"
		else
			echo "$i:dispari"
		fi
	done
else
	echo "Accetta solo valori numerici"
fi
```