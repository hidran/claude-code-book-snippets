# Capitolo 10 — Costruire una landing page end-to-end

## 🔁 Landing in 1 ora con Claude

```
Voglio costruire una landing page per [NOME PRODOTTO].

Descrizione del prodotto:
[2-3 frasi che descrivono il prodotto e il suo valore principale]

Audience:
[chi sono gli utenti target]

Call to action principale:
[es. "Inizia gratis", "Prenota una demo", "Scarica l'app"]

Sezioni da includere:
- Hero con titolo, sottotitolo, CTA e immagine/video
- Features (4-6 feature principali con icone)
- [sezione opzionale, es. "How it works" con 3 passi]
- Social proof (testimonial o loghi clienti)
- Pricing (N piani, con toggle mensile/annuale se presente)
- FAQ (6-8 domande più frequenti)
- Footer con CTA finale

Stile:
[es. "dark mode, accent viola, tipografia bold, tech forward"
 oppure "light, colori caldi, friendly, startup consumer"]

Stack:
React + Vite + Tailwind CSS (ultima versione)

Deploy target:
Firebase Hosting

Workflow:
1. Usa visual companion per mostrarmi 3 varianti di layout
2. Dopo l'approvazione del layout, genera le specifiche in docs/SPEC.md
3. Crea il piano in docs/PLAN.md con task atomici e criteri di done
4. Esegui un task alla volta, aspetta la mia conferma
5. Code review dopo tutti i componenti, prima del deploy
6. Build + firebase deploy --only hosting

Inizia dal Plan Mode. Non scrivere codice fino all'approvazione delle spec.
```

Questo prompt produce, in media, una landing completa in 60-90 minuti di sessione con conferme manuali, 45 minuti se usi il pattern subagent driven.
