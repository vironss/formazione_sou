**PORTSCANNER:** Supponiamo di avere 2 VM sul vostro laptop che riescano a "vedersi" lato rete. Scrivere uno script Bash che si comporti come un "port scanner" per capire quali porte TCP sono in ascolto sull'altra VM. E' richiesto di farlo tramite un ciclo che invochi il comando nc (NetCat) e non usando l'apposita feature di tale comando. E' inoltre gradita la customizzazione dell'ip/host target e del range di porte da linea di comando tramite argomenti e relativa sanificazione dell'input.

Soluzione:

```sh
 #! /usr/bin/env bash

>out.txt
re='^[0-9]{1,5}'
ip='\b((0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(0|1[0-9]{2}|[1-9][0-9]?|2[0-4][0-9]|25[0-5])\b'

if [[ $# != 3 ]]; then
	echo "Errore: Inserire tre valori"
	echo "Info parametri: ip inizio_porta fine_porta"
	exit 1
fi 

if ! [[ $1 =~ $ip ]]; then
	echo "Errore: Inserire un indirizzo ip valido"
	exit 2
fi
# prendo in input tre valori
if ! [[ $2 =~ $re && $3 =~ $re && $2 -lt "65536" && $3 -lt "65536" ]]; then
	echo "Errore: Inserire due valori compresi tra 1 e 65535"
	exit 3
fi

for i in $(seq $2 $3); do
	ncat -vi 1ms $1 $i &>> out.txt
done

echo "Le porte aperte nel range $2-$3 sono: "
cat out.txt | tr "." " " | awk -F ':' '$NF ~ /[0-9]+ $/ {print $NF}'
```

