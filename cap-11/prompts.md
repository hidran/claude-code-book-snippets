# Capitolo 11 — Photogallery: dal prompt al brief

## 🔁 Brief tecnico in 1 sessione

```
Contesto: sto costruendo [descrizione del progetto in 2-3 frasi].
Stack tecnologico: [lista dello stack scelto con motivazione].

Genera un brief tecnico strutturato che includa:
1. Functional requirements — features per ruolo (guest / utente / admin)
   con criteri di accettazione per ognuna
2. Non-functional requirements — performance (latenze obiettivo),
   sicurezza (autenticazione, autorizzazione, validazioni),
   scalabilità (ordine di grandezza degli utenti e dei dati attesi)
3. Constraints — stack bloccato, hosting target, budget indicativo,
   timeline
4. Decisioni tecniche chiave — auth strategy (JWT / sessions),
   upload strategy (diretta / presigned URL), DB approach
   (migrations / ORM / raw SQL), storage (locale / S3 / altro)
5. Quote e limiti — per utente (storage, numero oggetti, rate limit)
6. Audit log — operazioni da tracciare, retention

Genera un documento di 3-4 pagine in Markdown.
Dopo il draft, aspetta la mia revisione prima di procedere
con le specifiche operative.
```

Sostituisci i campi tra parentesi quadre con i dettagli del tuo progetto. Itera 2-3 volte prima di considerare il brief pronto.
