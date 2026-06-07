# Capitolo 12 — Spec Driven Development

## 🔁 Genera i file SDD da specifiche esistenti

```
Leggi i file [spec/db.md, spec/api.md, spec/frontend.md, spec/auth.md].

Genera i tre file canonici SDD nella cartella .spec/:

1. requirements.md — cosa costruire
   - Vision e what-it-is / what-it-is-not
   - Personas con user stories Given/When/Then
   - Acceptance criteria misurabili per ogni feature
   - Non-functional requirements (performance, sicurezza, scalabilità)
   - Out of scope esplicito
   - ID univoci REQ-XXX per ogni requisito

2. design.md — come costruirlo
   - Stack con versioni precise
   - Schema database completo (tabelle, colonne, vincoli, indici)
   - Contratti API (endpoint, DTO request, DTO response, error codes)
   - Pattern architetturale obbligatorio
   - Diagrammi Mermaid per i flussi critici
   - Riferimenti REQ-XXX per ogni sezione

3. tasks.md — la lista di lavoro
   - Task raggruppati in fasi
   - Ogni task: TASK-NNN, dipendenze, parallelizzabilità, owner, definition of done
   - Riferimenti a sezioni design.md e REQ-XXX
   - Status iniziale: [ ] per tutti

Poi genera build-workflow.md con:
- Fasi nell'ordine corretto con dipendenze esplicite
```
