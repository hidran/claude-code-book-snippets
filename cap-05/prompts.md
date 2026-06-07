# Capitolo 5 — Visualizzare i dati

## 🔁 Mini dashboard webapp

```
A partire da <csv_path>, crea una mini dashboard Flask:
- app.py con route GET / e GET /api/data
- templates/index.html con Chart.js CDN e tre canvas:
  <grafico1> (tipo: <line|bar|pie>),
  <grafico2> (tipo: <line|bar|pie>),
  <grafico3> (tipo: <line|bar|pie>)
- static/style.css con layout grid 2 colonne, font Inter,
  card bianche su sfondo grigio chiaro, responsive mobile
- Bottone "Aggiorna dati" che ri-fetcha /api/data e chiama
  chart.update() senza reload
Avvio: python app.py → server su http://localhost:5000
```

Sostituisci `<csv_path>`, `<grafico1/2/3>` e i tipi di grafico con i tuoi dati. Funziona su qualsiasi CSV tabellare.
