# Capitolo 4 — Da CSV a Excel

## 🔁 Excel report con pivot e formule

```
Leggi <file_csv>. Scrivi uno script Python tools/genera_excel.py che genera
<output.xlsx> con:

1. Sheet "Dati": tutti i dati del CSV come tabella filtrabile (auto_filter),
   intestazione con sfondo blu scuro (#1F4E78) e testo bianco in grassetto,
   larghezza colonne adattata al contenuto, freeze sulla prima riga,
   zebra striping sulle righe pari (#F2F2F2).

2. Sheet "Riepilogo": tabella pivot con <campo_righe> come righe e
   <campo_colonne> come colonne, valori = somma di <metrica>.
   Riga dei totali con formule SUM, non valori hardcoded.

3. Sheet "Grafici": un line chart per <metrica_temporale> nel tempo
   suddiviso per <segmentazione>, un pie chart per la distribuzione
   totale di <metrica> per <segmentazione>.

Usa openpyxl. Aggiungi argparse con --input, --output, --region (opzionale).
Se --output non specificato, usa report_YYYY-MM.xlsx con timestamp automatico.
Installa le dipendenze e aggiorna requirements.txt.
```
