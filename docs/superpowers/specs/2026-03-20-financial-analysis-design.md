# Finanzanalyse AAPL — Design Spezifikation

**Datum:** 2026-03-20
**Projekt:** financial-reporting-app
**Aufgabe:** Detailliertes Reporting für eine Aktie (Jupyter Notebook)

---

## Überblick

Detaillierte Finanzanalyse der Apple-Aktie (AAPL) über einen Zeitraum von 5 Jahren (2020–2024) in einem Jupyter Notebook. Das Notebook enthält ausgeführten Python-Code, deutsche Beschreibungen, statistische Analysen, Rendite- und Risikokennzahlen sowie interaktive Visualisierungen.

**Rahmenbedingungen:**
- Unternehmen: Apple Inc. (AAPL)
- Zeitraum: 01.01.2020 – 31.12.2024 (5 Jahre)
- Datenquelle: Yahoo Finance via `yfinance`
- Sprache: Deutsch (Markdown-Beschreibungen)
- Visualisierung: Plotly (interaktiv)
- Umgebung: Python 3.14, Jupyter Notebook (`sample.ipynb`)

---

## Notebook-Struktur (6 Abschnitte)

### Abschnitt 1: Datenbeschaffung & Aufbereitung

**Ziel:** AAPL-Rohdaten laden, bereinigen und erstmalig beschreiben.

**Inhalte:**
- `yfinance` Download: OHLCV-Daten für **AAPL** und **^GSPC** (S&P 500) gleichzeitig (01.01.2020 – 31.12.2024)
- Überprüfung auf fehlende Werte und Datumslücken
- Deskriptive Statistik (`.describe()`) mit Interpretation
- Übersichtstabelle der ersten/letzten Datensätze

---

### Abschnitt 2: Kursanalyse

**Ziel:** Preisentwicklung und Handelsvolumen visuell und statistisch untersuchen.

**Inhalte:**
- Interaktiver Kursverlauf (Schlusskurs 2020–2024) — Plotly Line Chart
- Handelsvolumen als Balkendiagramm
- Simple Moving Averages: SMA 50 und SMA 200 (Trendindikator)
- Bollinger Bands (20-Tage-Fenster, 2 Standardabweichungen)
- Candlestick-Chart des letzten Jahres (2024)

---

### Abschnitt 3: Renditeanalyse

**Ziel:** Renditen berechnen, statistisch charakterisieren und visualisieren.

**Inhalte:**
- Tägliche logarithmische Renditen (`log(P_t / P_{t-1})`)
- Kumulative Rendite über 5 Jahre (Plot)
- Histogramm der Renditeverteilung mit Normalverteilungskurve
- Rollierender 30-Tage-Durchschnitt der Renditen
- Jährliche Renditen je Kalenderjahr (Balkendiagramm)
- Kennzahlen: Durchschnittsrendite (täglich/annualisiert), Schiefe, Kurtosis

---

### Abschnitt 4: Risikoanalyse

**Ziel:** Risikoprofil von AAPL quantifizieren.

**Inhalte:**
- Historische Volatilität annualisiert, rollierend (30 und 60 Tage) — Plot
- Value at Risk (VaR): 95%- und 99%-Konfidenzniveau (historische Simulation)
- Maximum Drawdown (größter Kursverlust vom Hochpunkt)
- Sharpe Ratio (risikofreier Zinssatz: 4% p.a. → Tagesrate: `r_f_daily = 0.04 / 252`; berechnet auf Basis täglicher Renditen)
- Beta gegenüber S&P 500 (^GSPC)
- Korrelationsmatrix AAPL vs. S&P 500

---

### Abschnitt 5: Benchmarkvergleich

**Ziel:** AAPL-Performance relativ zum S&P 500 einordnen.

**Inhalte:**
- Kumulative Rendite AAPL vs. S&P 500 auf einem Chart
- Jährliche Renditen im Vergleich (gruppiertes Balkendiagramm)
- Rollierende Korrelation (60-Tage-Fenster)
- Rollierende Beta-Entwicklung über Zeit
- Scatter Plot: AAPL-Renditen vs. S&P 500-Renditen mit Regressionslinie

---

### Abschnitt 6: Zusammenfassung

**Ziel:** Alle Ergebnisse kompakt zusammenfassen.

**Inhalte:**
- Übersichtstabelle aller Kennzahlen (Rendite, Volatilität, Sharpe Ratio, Beta, VaR 95%/99%, Max Drawdown)
- Textliches Fazit (Markdown): Bewertung der AAPL-Aktie anhand der Ergebnisse
- Einschränkungen: Historische Daten sind keine Prognose

---

## Abhängigkeiten (requirements.txt)

```
yfinance
pandas
numpy
plotly
scipy
```

---

## Dateistruktur

```
financial-reporting-app/
├── sample.ipynb        # Hauptnotebook (wird vollständig ersetzt)
├── requirements.txt    # Abhängigkeiten
└── docs/
    └── superpowers/
        └── specs/
            └── 2026-03-20-financial-analysis-design.md
```

---

## Kennzahlen-Übersicht

| Kategorie | Kennzahl | Methode |
|-----------|----------|---------|
| Rendite | Durchschnittsrendite täglich | Arithmetisches Mittel log. Renditen |
| Rendite | Annualisierte Rendite | `exp(mean(log-Renditen) * 252) - 1` |
| Rendite | Kumulative Rendite | `exp(sum(log-Renditen)) - 1` |
| Rendite | Schiefe / Kurtosis | `scipy.stats` |
| Risiko | Historische Volatilität | Std. log. Renditen × √252 |
| Risiko | Value at Risk 95%/99% | Historische Simulation: 5. Perzentil (VaR 95%), 1. Perzentil (VaR 99%) |
| Risiko | Maximum Drawdown | `min((price / cummax(price)) - 1)` |
| Risiko | Sharpe Ratio | `(mean(r_tägl) - r_f_daily) / std(r_tägl) * √252`; `r_f_daily = 0.04/252` |
| Markt | Beta | Kovarianz(AAPL, GSPC) / Varianz(GSPC) |
| Markt | Korrelation | Pearson-Korrelation der Renditen |
