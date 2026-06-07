## Appendice C — Prompt Cheatsheet

50 prompt copia-incollabili categorizzati per scenario. Sostituisci i `<placeholder>` con i tuoi valori.

### Esplorazione progetto (5 prompt)

**P01 — Primo contatto con un progetto sconosciuto**
```
Leggi i file nel progetto e dimmi:
1. Quale stack tecnologico vedi (linguaggi, framework, package manager)
2. Quale parte sembra più recente vs vecchia
3. Quale file è il punto di ingresso (entry point)
4. Cosa NON capisci subito guardando i nomi delle cartelle
```

**P02 — Audit struttura cartelle**
```
Esplora la struttura del progetto. Per ogni top-level directory dimmi:
- Cosa contiene
- Quale convenzione organizzativa segue (per layer, per feature, mista)
- Eventuali incoerenze
```

**P03 — Trova il file responsabile di X**
```
Sto cercando dove viene gestito <funzionalità>. Esplora il progetto, identifica i file rilevanti (max 5), e spiegami il flusso in 3-5 righe.
```

**P04 — Dipendenze esterne usate**
```
Leggi package.json (o equivalente). Per ogni dipendenza non standard:
- A cosa serve nel progetto (grep nel codice se necessario)
- Quale alternativa avresti scelto tu se fossi al posto del primo dev
```

**P05 — Generare CLAUDE.md per il progetto**
```
Esplora il progetto, leggi i file di config principali, e genera un CLAUDE.md (max 200 righe) per la root. Includi: stack, convenzioni, comandi più usati, cose da NON fare. Solo ciò che cambia COME Claude scrive codice.
```

### Pianificazione (Plan Mode) (5 prompt)

**P06 — Plan task complesso**
```
Plan: voglio <obiettivo>. Stack: <stack>. Vincoli: <vincoli>.
Pianifica in passi numerati con: file impattati, ordine, dipendenze, criterio di "done" per ogni passo. Non scrivere codice.
```

**P07 — Plan refactoring**
```
Plan: voglio refactorare <area> per <motivazione>.
Identifica: 1) cosa cambia, 2) cosa NON deve cambiare (backward compat), 3) passi atomici, 4) test che proteggono dal regression.
```

**P08 — Plan migrazione tech**
```
Plan: migrare da <tech-A> a <tech-B>. Stack attuale: <stack>.
Strategia incrementale, fasi che lasciano sistema sempre in stato funzionante. No big-bang.
```

**P09 — Plan upgrade major version**
```
Plan: upgrade <libreria> dalla v<X> alla v<Y>.
Leggi i CHANGELOG/migration guide, identifica breaking changes per il NOSTRO codice, proponi fix step-by-step.
```

**P10 — Plan POC vs production**
```
Plan: voglio sperimentare <idea> SENZA committarmi alla soluzione finale.
Path POC (1 giorno): cosa minimo per validare l'idea.
Path Production (1 settimana): cosa per renderlo robusto.
```

### Refactoring (5 prompt)

**P11 — Estrarre funzione**
```
Refactor: nel file <file>, la funzione <fn> fa <troppo>. Estrai <responsabilità> in una funzione separata. Mantieni i test passing. Mostra solo il diff.
```

**P12 — Rinominare consistente**
```
Refactor: rinomina <oldName> in <newName> dovunque appaia (include doc/test/comments). Mostra preview di tutti i file impattati prima di eseguire.
```

**P13 — Riorganizzare imports**
```
Riorganizza gli import in <file> in 3 gruppi (1: stdlib/node_modules, 2: alias @app/*, 3: relativi ./). Ordine alfabetico dentro ogni gruppo. Rimuovi import non usati.
```

**P14 — Type tightening**
```
Audit i tipi in <file>. Trova: any nascosti, function senza return type esplicito, generic mancanti, union non esaustivi. Proponi fix con diff.
```

**P15 — Estrazione costanti magiche**
```
Trova numeri/stringhe magici in <area> che dovrebbero essere costanti nominate. Estrarre in un file <constants.ts>. Mostra diff.
```

### Bug fix (5 prompt)

**P16 — Diagnostica test fallito**
```
Il test <test-name> fallisce con <errore>. Diagnostica:
1. Leggi il test
2. Leggi il file sotto test
3. Identifica la causa (cambio API? bug? test obsoleto?)
4. Proponi fix (codice o test) con motivazione
```

**P17 — Reproduce bug locally**
```
Bug riportato: <descrizione>. Steps to reproduce: <steps>.
Verifica che il bug esista in locale (esegui i steps). Se sì, identifica il file/funzione responsabile.
```

**P18 — Diagnostica errore runtime**
```
Errore in produzione (stack trace):
<paste stack trace>
Diagnostica la causa probabile, identifica il commit che l'ha introdotto (git log/blame), proponi fix.
```

**P19 — Memory leak hunter**
```
La memoria del processo cresce in modo monotono. Cerca pattern tipici di leak: listeners non rimossi, closure che catturano scope grandi, cache senza TTL/eviction, connection pool che non rilasciano. Lista top 3 sospetti.
```

**P20 — Performance regression**
```
Endpoint <endpoint> è diventato lento (da 100ms a 800ms negli ultimi 7 giorni). Diagnostica:
1. Confronta le query SQL prima/dopo (N+1?)
2. Verifica indici tabelle coinvolte
3. Check log per warning
```

### Test (5 prompt)

**P21 — Test missing per funzione**
```
La funzione <fn> in <file> non ha test. Scrivi una suite Vitest/Jest che copre:
- Happy path
- Edge cases (input vuoto, null, valori limite)
- Error cases (input invalido)
Test devono essere indipendenti, no condivisione di stato.
```

**P22 — Test per regression bug**
```
Ho appena fixato il bug <descrizione> nel commit <hash>. Scrivi UN test (max) che fallirebbe se quel bug riapparisse.
```

**P23 — Coverage gap analysis**
```
Esegui coverage. Identifica i 3 file con coverage <50%. Per ognuno: quali path non sono coperti, quali sono i più critici da testare prima.
```

**P24 — E2E test critical flow**
```
Scrivi un test Playwright/Cypress per il flow <descrizione> (es. register → login → upload foto → logout). Test deve essere stabile (no sleep, usa waitFor). Cleanup dei dati creati alla fine.
```

**P25 — Mock vs integration**
```
Il test <test> usa molti mock. Decidi: meglio mockare o usare l'integration vera (es. test DB con docker-compose)? Trade-off: velocità vs realismo.
```

### Code Review (5 prompt)

**P26 — Wave review (4 agent)**
```
Dispatcha 4 agent in parallelo sul changeset HEAD vs main:
- security-auditor (vulnerabilità, validation, auth)
- performance-reviewer (N+1, bottleneck, memoria)
- api-consistency (REST conventions, errori, codici status)
- test-coverage (gap, edge cases)
Aggrega report. Output: critical/important/nice-to-have.
```

**P27 — Review architetturale**
```
Review architetturale del cambio recente. Verifica:
- SRP rispettato (un service una responsabilità)
- Boundary tra layer (controller → service → repo) non violati
- DIP rispettato (dipendi da astrazioni, non implementazioni)
- Niente leak di dettagli interni nelle API pubbliche
```

**P28 — Review naming**
```
Review naming del cambio. Cerca:
- Funzioni con nomi vaghi (process, handle, do, manage)
- Variabili con nomi una-lettera (eccetto i, j in loop)
- Booleani senza prefisso is/has/should
- Acronimi non standard
```

**P29 — Review test quality**
```
Review i test del cambio. Cerca:
- Test che testano implementazione invece di comportamento
- Test senza assert
- Test che dipendono da ordine di esecuzione
- Mock che mascherano bug
```

**P30 — Review accessibility**
```
Review accessibility del componente <component>:
- Semantic HTML (button vs div)
- ARIA label dove serve
- Keyboard navigation funzionante
- Contrast ratio >4.5:1
- Focus management nei modal
```

### Documentazione (5 prompt)

**P31 — README iniziale**
```
Genera un README.md per il progetto. Sezioni: cos'è, prerequisiti, install, run dev, build, test, deploy, contributing. Tone: pratico, comandi copia-incollabili.
```

**P32 — Documentazione endpoint API**
```
Per ogni endpoint in <controller>, genera doc OpenAPI 3.0:
- Path, method, summary
- Request body schema con esempi
- Response 2xx/4xx/5xx con schemi
- Auth requirements
```

**P33 — Aggiornare CHANGELOG.md**
```
Leggi git log dei commit dall'ultimo tag <v.X> a HEAD. Categorizza per: Features, Fixes, Breaking changes, Internal. Genera CHANGELOG.md sezione per la prossima release.
```

**P34 — Doc commenti su funzione complessa**
```
La funzione <fn> in <file> è complessa. Aggiungi JSDoc/docstring che spiega: cosa fa, parametri (con esempio), valore di ritorno, throw, edge cases note. Niente commenti sul COSA (è ovvio), solo sul PERCHÉ.
```

**P35 — Migration guide tra versioni**
```
Stiamo rilasciando v2.0. Genera MIGRATION.md per chi viene da v1.x: breaking changes, codepath che cambia, esempi prima/dopo per ognuno.
```

### DevOps / Deploy (5 prompt)

**P36 — Dockerfile multi-stage**
```
Genera Dockerfile multi-stage per <stack>. Stage 1: build (full dev deps). Stage 2: runtime (solo prod deps, non-root user, healthcheck). Ottimizza per cache layer.
```

**P37 — docker-compose dev environment**
```
Genera docker-compose.yml con: app, db (Postgres 16), redis, mailhog. Volumi per persistence, network bridge, health check, env vars in .env file.
```

**P38 — CI pipeline GitHub Actions**
```
Genera .github/workflows/ci.yml: trigger su PR + push main. Job: install, lint, type-check, test (con coverage report), build. Cache npm. Notify Slack on fail.
```

**P39 — CloudFormation skeleton**
```
Genera CloudFormation YAML per stack: ECS Fargate + RDS MySQL + ALB + S3 + CloudFront. Parameters: env, app name, db password (no-echo). Outputs: ALB URL, CloudFront URL.
```

**P40 — Healthcheck endpoint completo**
```
Genera endpoint /health che ritorna 200 se: DB raggiungibile (SELECT 1), Redis raggiungibile (PING), filesystem writable. Altrimenti 503 con dettagli per ogni check.
```

### Security (5 prompt)

**P41 — Audit security headers**
```
Audit i security headers dell'app. Verifica: HSTS, CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy, Permissions-Policy. Per ogni mancante: configurazione raccomandata.
```

**P42 — Rate limiting strategy**
```
Pianifica rate limiting per gli endpoint critici: /login (anti-bruteforce), /register (anti-spam), /api/* (anti-abuse). Per ognuno: limit, finestra, identificatore (IP o user).
```

**P43 — Audit dependency vulnerabilities**
```
Esegui npm audit (o pip audit / cargo audit). Lista vulnerabilità per severità. Per ognuna: tipo, fix disponibile, breaking change?
```

**P44 — Secrets in code scan**
```
Cerca segreti hardcoded nel repo (API keys, password, token, JWT secret). Pattern: stringhe lunghe alfanumeriche in codice (no test/example). Riporta file:line.
```

**P45 — Input validation gap**
```
Audit endpoint POST/PUT/PATCH. Verifica che ognuno abbia: DTO con validation, sanitization se output user-generated, size limit, type strict. Lista gap.
```

### Refactoring DB (5 prompt)

**P46 — Aggiungere indice**
```
Query <query> è lenta. Analizza EXPLAIN, identifica missing index, proponi migration SQL per aggiungerlo (idempotente se già esiste).
```

**P47 — Migration schema sicura**
```
Voglio aggiungere colonna <col> alla tabella <table>. Migration deve essere zero-downtime: aggiunta nullable prima, backfill, set not-null in seconda migration. Mostra entrambe.
```

**P48 — Foreign key audit**
```
Audit foreign keys del schema. Verifica: ogni relazione ha FK costraint, ogni FK ha indice corrispondente, ON DELETE behavior intenzionale (CASCADE? SET NULL? RESTRICT?).
```

**P49 — Soft delete pattern**
```
Aggiungi soft delete a <tabella>: colonna deleted_at, scope di default che esclude righe deleted, metodo restore(), test di entrambi.
```

**P50 — N+1 query hunter**
```
Esegui endpoint <endpoint> sotto profiler. Identifica query N+1. Proponi fix con eager loading (Include/With/.preload).
```
