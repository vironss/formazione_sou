**EXTENDED REGEX:** Utilizzare il comando egrep per risolvere i seguenti esercizi (dando esempi di possibili input):

- Matchare sequenze alfabetiche di almeno un carattere, sia maiuscole che minuscole
- Togliere tutte le righe di commento di uno script Bash matchando le righe che iniziano con '#'
- Matchare in un file le righe che contengono sequenze di 'a' ripetute da 3 a 6 volte
- Matchare in un file tutte le righe che contengono una delle seguenti parole: apple, pear, orange

Soluzione:
1. 
```sh
$ cat es7.txt
#commento 1..%&/()=
# commento 2 parola
!"£$%&/()
1234567890
testo testo testo2
s
sss
sss3232gtgg32
òadsàadas
12322fsdfdf ndfsfdsf
```

```bash
$ egrep "[a-zA-Z]+" es7.txt 
#commento 1..%&/()=
# commento 2 parola
testo testo testo 2
s
sss
sss3232gtgg32
òadsàadas
12322fsdfdf ndfsfdsf
```


2. `-i` per modifica diretta su file
```sh
$ cat -n es7_2.txt 
	1 #commento 1...£$%&/()
	2 # commento 2 parola
	3 testo testo 
	4 commento dietro testo #a commento
	5
```

```sh
$ sed -i -E '/^#.*/d' es7_2.txt 
$ cat es7_2.txt
    1 testo testo 
    2 commento dietro testo 
    3
```

3. 
```sh
$ cat es7_3.txt 
ciaaao
ciiiaaaaaaaiooo
aabbce
aabbccccaaaa
aabaababaaaaa
aaaaa
aaaacccdcccaaaaaaa
```

```sh 
$ egrep "[^a]a{3,6}[^a]|^a{3,6}[^a]|[^a]a{3,6}$" es7_3.txt 
ciaaao
aabbccccaaaa
aabaababaaaaa
aaaacccdcccaaaaaaa
```

4. 
```sh
$ cat es7_4.txt 
pear di apple e orange
Orange, Apple e pear 
apple, orange e Pear
Pear, Orange e Apple
apples, orangesss, pears
```
caso 1: prendo qualsiasi comparsa nel testo
```sh
egrep "apple|orange|pear" es7_4.txt 
pear di apple e orange
Orange, Apple e pear 
apple, orange e Pear
apples, orangesss, pears
```
caso 2: prendo solo parole intere
```sh
egrep "[^\w](apple|pear|orange)[^\w]|^(apple|pear|orange)[^\w]|[^\w](apple|pear|orange)$" es7_4.txt
```