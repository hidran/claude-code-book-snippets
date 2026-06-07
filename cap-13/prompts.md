# Capitolo 13 — Execution & Code Review

## 🔁 Wave review 4-agent

```
Wave review di [nome della wave] (task [inizio]-[fine]).
Dispatcha quattro agenti in parallelo:

1. security-auditor
   Cerca: auth bypass, input validation mancante, esposizione
   dati non autorizzata, segreti hardcoded, CORS troppo permissivo.
   Tools: Read, Grep. Modello: Sonnet.

2. performance-reviewer
   Cerca: N+1 query, eager loading mancante, indici DB assenti su
   colonne filtrate, operazioni sincrone che dovrebbero essere job.
   Tools: Read, Grep. Modello: Sonnet.

3. api-consistency
   Cerca: incoerenza nell'error envelope, status code sbagliati,
   controller che non usano il query object, naming non uniforme.
   Tools: Read, Grep. Modello: Sonnet.

4. test-coverage
   Cerca: path critici senza test, edge case mancanti, test che
   bypassano la policy, N+1 nei test, factory incomplete.
   Tools: Read, Grep. Modello: Sonnet.

Per ogni finding: file, riga, severità (CRITICAL/HIGH/MAJOR/MEDIUM/LOW),
fix proposto. Aggrega i quattro report in ordine di priorità.
```

Adatta [nome della wave] e l'intervallo di task al tuo progetto. Funziona su qualsiasi stack — Laravel, NestJS, Django, Rails.
