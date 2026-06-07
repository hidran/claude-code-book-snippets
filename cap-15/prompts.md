# Capitolo 15 — Pre-deploy QA & Multi-LLM Review

## 🔁 Genera checklist pre-deploy

```
Sei un QA engineer senior. Il mio progetto è [descrivi stack e tipo di app].
Genera una checklist pre-deploy strutturata per categoria:
Funzionale, Performance, Security, Data Integrity, Observability.
Per ogni voce specifica: cosa verificare, come verificarlo (comando o azione),
criterio di successo. Formato: tabella Markdown.
```

---

## 🔁 Cross-LLM Review (copia questo in Claude, Gemini, Codex e Kimi)

```
Agisci come un senior software engineer con 10+ anni di esperienza.
Fai una critical review del seguente codice.

Valuta su questi assi:
1. Best practices e standard del linguaggio/framework
2. Principi SOLID e design patterns (SRP, OCP, LSP, ISP, DIP)
3. Sicurezza (injection, autenticazione, autorizzazione, esposizione dati)
4. Scalabilità e performance (query N+1, uso memoria, caching)
5. Affidabilità e gestione degli errori (exception handling, rollback)
6. Edge case non gestiti (input limite, concorrenza, stati intermedi)

Per ogni problema:
- Gravità: Critical / High / Medium / Low
- File e riga (se applicabile)
- Descrizione concisa del problema
- Fix consigliato con snippet di codice

Output: lista Markdown ordinata per gravità decrescente.
Non fare padding: se non trovi problemi in un'area, dillo esplicitamente.

[incolla qui il diff git o i file da revisionare]
```
