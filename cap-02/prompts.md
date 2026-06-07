# Capitolo 2 — I primi prompt utili

## 🔁 Template prompt: aggiungere una feature

```
Contesto: [cosa esiste, quale file, quale funzione, perché esiste]

Obiettivo: [cosa deve cambiare o essere creato, in modo misurabile]

Vincoli:
- Non modificare [file/API/comportamento]
- Segui il pattern già usato in [file di riferimento]
- [Altre limitazioni: versione Node, dipendenze, compatibilità]

Esempi: leggi [file esistente] per il pattern da seguire

Output: [prima mostrami il piano / crea il file / mostrami solo il diff]
```

---

## 🔁 Refactoring guidato

```
Contesto: leggi [percorso file]. La funzione/classe [nome] fa [descrizione
di cosa fa e perché esiste attualmente].

Obiettivo: [cosa deve cambiare, in modo misurabile. Es: separare le
responsabilità in X funzioni pure / rendere la classe testabile con mock /
eliminare la dipendenza da [libreria]]

Vincoli:
- La firma pubblica di [funzione/interfaccia] deve restare identica
- Non toccare [file o cartella correlata]
- I test in [percorso test] devono continuare a passare senza modifiche

Esempio di pattern target: guarda [file che ha già lo stile che vuoi]

Output: prima mostrami un piano numerato con i passi e i file impattati.
Non eseguire finché non approvo.
```

Sostituisci le parti tra parentesi quadre con i dettagli del tuo caso. Funziona per qualunque tipo di refactoring, dalla semplice separazione di responsabilità alla riscrittura di un modulo intero.
