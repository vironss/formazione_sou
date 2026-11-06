
**1 -**  `Esercizio 1`

Creare un file in /tmp e chiamarlo app.log
Mettersi in tail su questo file e al tempo stesso iniziare a direzionare dell’output all’interno del file con questa dicitura:
 Error: descrizione errore,
“ Info: descrizione info”
vedere cosa succede al file in tail.
Aggiungere almeno 2 righe di ogni tipologia di messaggio
Una volta terminato di direzionare l’output e accertatosi che il file non sia vuoti, eseguire tramite il comando grep la ricerca degli errori contenuti nel file

Soluzione:
	creazione del file: `touch /tmp/app.log` 
	---
	riempimento tipo 1 del file: `for i in {1..10}; do { echo "Errore: errore generale $i"; sleep 1; echo "Info:info generale $i"; sleep 1; }; done >> /tmp/app.log`
	---
	riempimento tipo 2 del file: scrittura di comandi sbagliati e di nuovo appesi in tmp/app2.log
	---
	`grep -Eir "error|info" /tmp/app.log`
	# uso -i per non considerare il case sensitive, -r per stampare tutta la riga dove si trova la parola di ricerca
	---
	Output comando:
		![[Screenshot 2026-10-30 alle 17.48.05.png|354]]


**2 -** `Esercizio 2`

All’interno di una specifica directory a vostra scelta ( non vuota e con diversi file di dimensioni diverse) dovete cercare tutti i file che superano una dimensione di 1 MB, e 10 MB . Spiegatemi quale comando usereste

Soluzione:
	# uso find perché è l'unico che conosco/ricordo che cerca anche per dimensione
	Comando `find` con opzione `-size`
	es: `find . -size +10M` o `find . -size +1M` 
	Output comando:
	![[Screenshot 2026-11-02 alle 09.12.03.png|237]]![[Screenshot 2026-11-02 alle 09.14.02.png|362]]
	Files:
	![[Screenshot 2026-11-02 alle 09.14.51.png|356]]

**3 -** `Esercizio 3`

passatemi l'output di questi comandi:
lsblk
df -h
ls -l /dev/disk/by-uuid
cat /etc/fstab
ridirezionate l'output di tutti i comandi appendendo l'output di ogni singolo comando in un file OUT.LOG
bonus se il comando lo fate con un one-liner


Soluzioni:
	# dopo considerazione di varie possibilità, ho optato per questa:
	`(lsblk; df -h; ls -l /dev/disk/by-uuid; cat /etc/fstab;) >> out.log`
	# Ho fatto una semplice concatenazione di comandi e direzionato l'output nel file tramite il simbolo >> append