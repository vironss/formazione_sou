**Esercizio 1**
- **Touch:** Illustrare almeno 2 casi in cui il comando touch può generare una condizione di errore.
**caso 1**: scrivendo solo touch senza operazioni o file input
```bash
[viron@localhost touchtest]$ touch
touch: manca il file operando
Try 'touch --help' for more information.
```

**caso 2**: dare un valore sbagliato ad una opzione:
```bash
[viron@localhost touchtest]$ touch -r pr prova
touch: recupero degli attributi di 'pr' non riuscito: File o directory non esistente
```

```bash
[viron@localhost touchtest]$ touch -t 13-01-2025 18:12:23 prova
touch: formato di data "13-01-2025" non valido
```

**caso 3**: non può toccare file in cartelle che non esistono
```bash
[viron@localhost touchtest]$ touch /prova/file
touch: impossibile fare touch di '/prova/file': File o directory non esistente
```

**caso 4**: errore di permessi 
```bash
[viron@localhost touchtest]$ touch prova
touch: impossibile fare touch di 'prova': Permesso negato
```
