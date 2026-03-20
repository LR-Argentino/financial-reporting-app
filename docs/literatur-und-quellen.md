# Literatur & Quellen — Finanzanalyse AAPL

Dieses Dokument enthält alle wissenschaftlichen Quellen, Lehrbücher und Online-Ressourcen, die den im Notebook verwendeten Konzepten und Methoden zugrunde liegen. Die Gliederung folgt der Struktur des Notebooks.

---

## 1. Datenbeschaffung & Datenaufbereitung

### Warum Datenaufbereitung notwendig ist

Rohdaten aus Finanzquellen enthalten häufig fehlende Werte (z.B. an Feiertagen), Ausreißer oder Inkonsistenzen. Eine sorgfältige Aufbereitung ist Voraussetzung für valide Analyseergebnisse.

**Lehrbücher:**

- Fahrmeir, L., Künstler, R., Pigeot, I., & Tutz, G. (2016). *Statistik: Der Weg zur Datenanalyse* (8. Aufl.). Springer. — Grundlagen deskriptiver Statistik und Datenaufbereitung.

- Pandas Development Team. (2024). *pandas: Powerful Python Data Analysis Library* (Dokumentation). pandas.pydata.org — Referenz für `.describe()`, `.isnull()`, `.dropna()`.

**Datenbeschaffung — Yahoo Finance / yfinance:**

- Aroussi, R. (2019–2024). *yfinance: Yahoo! Finance market data downloader* [Python-Bibliothek]. GitHub: ranaroussi/yfinance — Offizielle Bibliothek zur Abfrage von Börsendaten über die Yahoo Finance API.

- Yahoo Finance. *Historical Data*. finance.yahoo.com — Primäre Datenquelle für OHLCV-Kursdaten (Open, High, Low, Close, Volume).

**OHLCV-Daten (Open, High, Low, Close, Volume):**

- Murphy, J.J. (1999). *Technical Analysis of the Financial Markets*. New York Institute of Finance. — Erklärt die Bedeutung der OHLCV-Datenstruktur für die Chartanalyse (Kapitel 1–2).

---

## 2. Kursanalyse

### Moving Averages (SMA 50 / SMA 200)

Ein Simple Moving Average (SMA) glättet Kursschwankungen und zeigt den Trend. Der SMA 50 gilt als kurzfristiger, der SMA 200 als langfristiger Trendindikator. Die Kreuzung beider ("Golden Cross" / "Death Cross") ist ein klassisches Handelssignal.

**Quellen:**

- Murphy, J.J. (1999). *Technical Analysis of the Financial Markets* (Kap. 9: Moving Averages). New York Institute of Finance.

- Appel, G. (2005). *Technical Analysis: Power Tools for Active Investors*. Financial Times Press. — Enthält detaillierte Erklärungen zu gleitenden Durchschnitten.

- Investopedia. *Simple Moving Average (SMA)*. investopedia.com/terms/s/sma.asp

### Bollinger Bands

Bollinger Bands, entwickelt von John Bollinger, bestehen aus einem 20-Tage-SMA (Mittellinie) sowie oberer und unterer Bande im Abstand von 2 Standardabweichungen. Sie messen relative Volatilität und zeigen überkaufte/überverkaufte Marktlagen an.

**Quellen:**

- Bollinger, J. (2002). *Bollinger on Bollinger Bands*. McGraw-Hill. — Originalquelle von John Bollinger selbst.

- Murphy, J.J. (1999). *Technical Analysis of the Financial Markets* (Kap. 21). New York Institute of Finance.

- Investopedia. *Bollinger Band*. investopedia.com/terms/b/bollingerbands.asp

### Candlestick-Charts

Candlestick-Charts stellen die vier Kursebenen (Open, High, Low, Close) eines Zeitraums visuell dar und stammen ursprünglich aus dem japanischen Reishandel des 18. Jahrhunderts.

**Quellen:**

- Nison, S. (1991). *Japanese Candlestick Charting Techniques*. New York Institute of Finance. — Standardwerk zu Candlestick-Charts.

- Murphy, J.J. (1999). *Technical Analysis of the Financial Markets* (Kap. 12). New York Institute of Finance.

---

## 3. Renditeanalyse

### Was ist eine Rendite?

Die Rendite (engl. *return*) ist der prozentuale Gewinn oder Verlust einer Kapitalanlage über einen bestimmten Zeitraum, bezogen auf den eingesetzten Betrag. Sie ist die zentrale Größe zur Bewertung von Investitionen.

**Grundlegende Quellen:**

- Brealey, R.A., Myers, S.C., & Allen, F. (2023). *Principles of Corporate Finance* (14. Aufl.). McGraw-Hill. — Kapitel 7 und 8 behandeln Rendite und Risiko aus Unternehmensperspektive.

- Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl.). McGraw-Hill. — Kapitel 5 ("Risk, Return, and the Historical Record") ist das Standardkapitel zu Renditeberechnung.

- Fabozzi, F.J., & Markowitz, H.M. (Hrsg.). (2011). *The Theory and Practice of Investment Management* (2. Aufl.). Wiley. — Umfassende akademische Behandlung von Rendite- und Risikokonzepten.

### Logarithmische vs. einfache Renditen

Logarithmische Renditen (`log(P_t / P_{t-1})`) sind über Zeit additiv und nähern sich besser einer Normalverteilung als einfache Prozentrenditen. Sie sind der Standard in der wissenschaftlichen Finanzliteratur.

**Quellen:**

- Campbell, J.Y., Lo, A.W., & MacKinlay, A.C. (1997). *The Econometrics of Financial Markets*. Princeton University Press. — Kapitel 1 erklärt die Verwendung logarithmischer Renditen ausführlich.

- Hull, J.C. (2022). *Options, Futures, and Other Derivatives* (11. Aufl.). Pearson. — Kapitel 15 begründet die Nutzung log-normaler Renditen.

- Cont, R. (2001). Empirical properties of asset returns: stylized facts and statistical issues. *Quantitative Finance, 1*(2), 223–236. — Empirische Eigenschaften von Aktienrenditen (Schiefe, Kurtosis, Fat Tails).

### Annualisierung von Renditen

Die annualisierte Rendite erlaubt den Vergleich von Renditen unterschiedlicher Zeiträume auf Jahresbasis.

- Formel: `exp(mean(log-Renditen) * 252) - 1` (252 = durchschnittliche Anzahl Handelstage pro Jahr)

**Quellen:**

- Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl., Kap. 5). McGraw-Hill.

- Fabozzi, F.J. (2007). *Fixed Income Analysis* (2. Aufl.). CFA Institute. — Enthält Abschnitt zur Renditeannualisierung.

### Schiefe und Kurtosis (statistische Momente)

Schiefe (Skewness) beschreibt die Asymmetrie einer Verteilung; negative Schiefe bedeutet häufigere Verluste als die Normalverteilung vorhersagt. Kurtosis (Wölbung) misst die "Schweifdicke" der Verteilung — hohe Kurtosis bedeutet häufigere Extremereignisse ("Fat Tails").

**Quellen:**

- Cont, R. (2001). Empirical properties of asset returns: stylized facts and statistical issues. *Quantitative Finance, 1*(2), 223–236.

- Fahrmeir, L. et al. (2016). *Statistik: Der Weg zur Datenanalyse* (8. Aufl., Kap. 3). Springer. — Deutsche Einführung in statistische Momente.

---

## 4. Risikoanalyse

### Was ist Risiko in der Finanzanalyse?

In der Finanzwissenschaft wird Risiko typischerweise als Schwankungsbreite (Volatilität) der Renditen gemessen. Ein höheres Risiko bedeutet größere Unsicherheit über zukünftige Renditen.

**Quellen:**

- Markowitz, H.M. (1952). Portfolio Selection. *The Journal of Finance, 7*(1), 77–91. — Grundlegendes Paper, das Risiko als Standardabweichung der Renditen definiert. Basis der modernen Portfoliotheorie.

- Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl., Kap. 6–7). McGraw-Hill.

### Historische Volatilität

Die Volatilität misst die Streuung der täglichen Renditen. Die Annualisierung erfolgt durch Multiplikation mit √252 (Anzahl Handelstage).

**Quellen:**

- Hull, J.C. (2022). *Options, Futures, and Other Derivatives* (11. Aufl., Kap. 15). Pearson.

- Natenberg, S. (1994). *Option Volatility and Pricing*. McGraw-Hill. — Praxisnahe Erklärung historischer und impliziter Volatilität.

### Value at Risk (VaR)

Der Value at Risk (VaR) gibt an, welcher Verlust mit einer bestimmten Wahrscheinlichkeit an einem Handelstag nicht überschritten wird. VaR 95% bedeutet: In 95% aller Fälle ist der Tagesverlust geringer als dieser Wert.

**Quellen:**

- Jorion, P. (2007). *Value at Risk: The New Benchmark for Managing Financial Risk* (3. Aufl.). McGraw-Hill. — Das Standardwerk zum Value at Risk.

- Basel Committee on Banking Supervision. (2019). *Minimum capital requirements for market risk*. Bank for International Settlements (BIS). — Regulatorischer Kontext der VaR-Anwendung in Banken.

- Investopedia. *Value at Risk (VaR)*. investopedia.com/terms/v/var.asp

### Maximum Drawdown

Der Maximum Drawdown (MDD) misst den größten Kursverlust vom bisherigen Höchststand bis zum darauffolgenden Tiefststand. Er ist eine wichtige Kennzahl für Investoren zur Beurteilung des Worst-Case-Szenarios.

- Formel: `min((Kurs_t / max(Kurs_{0..t})) - 1)`

**Quellen:**

- Magdon-Ismail, M., & Atiya, A.F. (2004). Maximum drawdown. *Risk Magazine, 17*(10), 99–102.

- Investopedia. *Maximum Drawdown (MDD)*. investopedia.com/terms/m/maximum-drawdown.asp

### Sharpe Ratio

Die Sharpe Ratio misst die risikoadjustierte Rendite: Wie viel Mehrrendite (über dem risikofreien Zinssatz) wird pro Einheit Risiko (Volatilität) erzielt? Eine Sharpe Ratio > 1 gilt als gut, > 2 als sehr gut.

- Formel: `(R_p - R_f) / σ_p` (annualisiert)

**Quellen:**

- Sharpe, W.F. (1966). Mutual Fund Performance. *The Journal of Business, 39*(1), 119–138. — Originalveröffentlichung der Sharpe Ratio.

- Sharpe, W.F. (1994). The Sharpe Ratio. *The Journal of Portfolio Management, 21*(1), 49–58. — Überarbeitete und präzisierte Definition.

- Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl., Kap. 24). McGraw-Hill.

### Beta — Marktrisiko (CAPM)

Das Beta misst die Sensitivität einer Aktie gegenüber dem Gesamtmarkt. Beta = 1 bedeutet: Die Aktie bewegt sich wie der Markt. Beta > 1 bedeutet überproportionale Reaktion.

- Formel: `β = Cov(R_AAPL, R_Markt) / Var(R_Markt)`

**Quellen:**

- Sharpe, W.F. (1964). Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk. *The Journal of Finance, 19*(3), 425–442. — Originalquelle des CAPM und Beta-Konzepts.

- Lintner, J. (1965). The Valuation of Risk Assets and the Selection of Risky Investments in Stock Portfolios and Capital Budgets. *The Review of Economics and Statistics, 47*(1), 13–37.

- Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl., Kap. 9: The Capital Asset Pricing Model). McGraw-Hill.

---

## 5. Benchmarkvergleich (S&P 500)

### Warum ein Benchmark?

Ein Benchmark ist ein Referenzindex, gegen den die Performance einer Aktie oder eines Portfolios bewertet wird. Der S&P 500 ist der gängigste Benchmark für US-amerikanische Aktien.

**Quellen:**

- Malkiel, B.G. (2023). *A Random Walk Down Wall Street* (13. Aufl.). W.W. Norton & Company. — Kap. 1 und 12 erläutern die Bedeutung von Marktindizes als Benchmark.

- S&P Dow Jones Indices. *S&P 500 Index Methodology*. spglobal.com/spdji — Offizielle Methodikbeschreibung des S&P 500 Index.

- Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl., Kap. 24: Portfolio Performance Evaluation). McGraw-Hill.

### Rollierende Korrelation und Beta

Rollierende Kennzahlen zeigen, wie sich die Beziehung zwischen AAPL und dem Markt im Zeitverlauf verändert hat — insbesondere in Krisenzeiten (z.B. COVID-2020).

**Quellen:**

- Campbell, J.Y., Lo, A.W., & MacKinlay, A.C. (1997). *The Econometrics of Financial Markets* (Kap. 2). Princeton University Press.

---

## 6. Python-Bibliotheken (technische Dokumentation)

| Bibliothek | Verwendungszweck | Offizielle Dokumentation |
|------------|-----------------|--------------------------|
| `yfinance` | Datenbeschaffung von Yahoo Finance | github.com/ranaroussi/yfinance |
| `pandas` | Datenaufbereitung, Zeitreihenanalyse | pandas.pydata.org/docs |
| `numpy` | Numerische Berechnungen (Kovarianz, Logarithmus, Wurzel) | numpy.org/doc |
| `plotly` | Interaktive Visualisierungen | plotly.com/python |
| `scipy.stats` | Statistische Funktionen (Normalverteilung, Schiefe, Kurtosis) | docs.scipy.org/doc/scipy |

---

## 7. Weiterführende Online-Ressourcen (Deutsch)

| Ressource | Inhalt | URL |
|-----------|--------|-----|
| Investopedia (DE-verfügbar) | Definitionen aller Finanzkennzahlen | investopedia.com |
| Bundesbank — Bildungsportal | Erklärung von Aktien, Rendite, Risiko | bundesbank.de |
| Boerse ARD | Deutsche Börsennachrichten & Glossar | boerse.ard.de |
| Statista | Marktdaten und Statistiken | statista.com |
| CFA Institute | Lernmaterialien zu Investments & Analyse | cfainstitute.org |

---

## 8. Vollständiges Literaturverzeichnis (Alphabetisch)

Bodie, Z., Kane, A., & Marcus, A.J. (2023). *Investments* (13. Aufl.). McGraw-Hill.

Bollinger, J. (2002). *Bollinger on Bollinger Bands*. McGraw-Hill.

Brealey, R.A., Myers, S.C., & Allen, F. (2023). *Principles of Corporate Finance* (14. Aufl.). McGraw-Hill.

Campbell, J.Y., Lo, A.W., & MacKinlay, A.C. (1997). *The Econometrics of Financial Markets*. Princeton University Press.

Cont, R. (2001). Empirical properties of asset returns: stylized facts and statistical issues. *Quantitative Finance, 1*(2), 223–236.

Fabozzi, F.J., & Markowitz, H.M. (Hrsg.). (2011). *The Theory and Practice of Investment Management* (2. Aufl.). Wiley.

Fahrmeir, L., Künstler, R., Pigeot, I., & Tutz, G. (2016). *Statistik: Der Weg zur Datenanalyse* (8. Aufl.). Springer.

Hull, J.C. (2022). *Options, Futures, and Other Derivatives* (11. Aufl.). Pearson.

Jorion, P. (2007). *Value at Risk: The New Benchmark for Managing Financial Risk* (3. Aufl.). McGraw-Hill.

Lintner, J. (1965). The Valuation of Risk Assets and the Selection of Risky Investments in Stock Portfolios and Capital Budgets. *The Review of Economics and Statistics, 47*(1), 13–37.

Magdon-Ismail, M., & Atiya, A.F. (2004). Maximum drawdown. *Risk Magazine, 17*(10), 99–102.

Malkiel, B.G. (2023). *A Random Walk Down Wall Street* (13. Aufl.). W.W. Norton & Company.

Markowitz, H.M. (1952). Portfolio Selection. *The Journal of Finance, 7*(1), 77–91.

Murphy, J.J. (1999). *Technical Analysis of the Financial Markets*. New York Institute of Finance.

Nison, S. (1991). *Japanese Candlestick Charting Techniques*. New York Institute of Finance.

Sharpe, W.F. (1964). Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk. *The Journal of Finance, 19*(3), 425–442.

Sharpe, W.F. (1966). Mutual Fund Performance. *The Journal of Business, 39*(1), 119–138.

Sharpe, W.F. (1994). The Sharpe Ratio. *The Journal of Portfolio Management, 21*(1), 49–58.
