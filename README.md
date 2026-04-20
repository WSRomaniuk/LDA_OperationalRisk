# Operational Risk Capital Estimation – AMA / LDA Approach

A comprehensive actuarial analysis estimating the 99.9% Operational Value at Risk (OpVaR) and Expected Shortfall (OpES) for a commercial bank using the Loss Distribution Approach (LDA) under Advanced Measurement Approaches (AMA). The project was implemented in R.

## Repository Contents

* **OpVaR_LDA.Rmd** – Source code of the analysis in R Markdown format (data preparation, distribution fitting, Monte Carlo simulation, and sensitivity analysis).
* **OpVaR_LDA.html** – The generated, ready-to-read report containing statistical tests, simulated values, and conclusions.
* **plik13.csv** – The dataset containing historical gross loss amounts categorized by operational risk event types (business lines) over several years.

## Main Results

The evaluation highlights the critical importance of individual distribution fitting for different business lines:

* **Original (Mixed) Model:** Yielded a realistic OpVaR of approximately **23M PLN**. This model optimally assigned specific distributions (e.g., Lognormal for *Commercial Banking*, Weibull for others) based on Anderson-Darling, KS, and AIC tests, capturing the true "fat-tail" nature of specific extreme events.
* **Sensitivity Analysis (Forced Distributions):**
    * **Lognormal Only:** Gross overestimation (OpVaR ~83M PLN), leading to severe capital inefficiency.
    * **Exponential Only:** Severe underestimation (OpVaR ~8M PLN) due to a "light tail", ignoring catastrophic risk entirely.
    * **Weibull Only:** Underestimation (OpVaR ~2.4M PLN) caused by the MLE algorithm fitting a shape parameter > 1, truncating the distribution tail.
* **Methodological Conclusion:** Implementing a "one-size-fits-all" severity distribution across all banking lines leads either to fatal undercapitalization or extreme cost inefficiency. The multi-iteration Monte Carlo method (n=10) demonstrated high model stability for the mixed approach (low standard deviation).

## Technologies

* R (packages: `fitdistrplus`, `MASS`)
* R Markdown
* Monte Carlo Simulation

---

# Szacowanie Kapitału na Ryzyko Operacyjne – Podejście AMA / LDA

Kompleksowa analiza aktuarialna szacująca Wartość Narażoną na Ryzyko Operacyjne (99,9% OpVaR) oraz Oczekiwany Niedobór (OpES) dla banku komercyjnego przy użyciu metody LDA (Loss Distribution Approach) w ramach zaawansowanych metod pomiaru (AMA). Projekt został zrealizowany w języku R.

## Zawartość repozytorium

* **OpVaR_LDA.Rmd** – Kod źródłowy analizy w formacie R Markdown (przygotowanie danych, dopasowywanie rozkładów, symulacja Monte Carlo i analiza wrażliwości).
* **OpVaR_LDA.html** – Wygenerowany, gotowy do odczytu raport zawierający testy statystyczne, wyliczone wartości symulacyjne i wnioski.
* **plik13.csv** – Zbiór danych zawierający historyczne wartości strat brutto z podziałem na kategorie zdarzeń ryzyka operacyjnego (linie biznesowe) na przestrzeni kilku lat.

## Główne wyniki

Badanie dowodzi krytycznego znaczenia indywidualnego dopasowania rozkładów dla poszczególnych linii biznesowych:

* **Model Oryginalny (Mieszany):** Wygenerował realistyczny OpVaR na poziomie ok. **23 mln PLN**. Model ten optymalnie przypisał specyficzne rozkłady (np. Log-normalny dla *Commercial Banking*, Weibulla dla pozostałych) na podstawie testów Andersona-Darlinga, KS i kryterium AIC, prawidłowo wychwytując naturę "grubych ogonów" dla zdarzeń ekstremalnych.
* **Analiza Wrażliwości (Rozkłady Wymuszone):**
    * **Tylko Log-normalny:** Drastyczne przeszacowanie (OpVaR ~83 mln PLN), prowadzące do zamrożenia zbyt dużej ilości kapitału (nieefektywność).
    * **Tylko Wykładniczy:** Poważne niedoszacowanie (OpVaR ~8 mln PLN) z powodu "lekkiego ogona", ignorującego ryzyko katastroficzne.
    * **Tylko Weibull:** Niedoszacowanie (OpVaR ~2,4 mln PLN) wynikające z faktu, że algorytm MLE dopasował parametr kształtu > 1, sztucznie ucinając ogon rozkładu.
* **Wniosek Metodologiczny:** Wymuszenie jednego typu rozkładu dotkliwości dla wszystkich linii banku prowadzi do katastrofalnego niedoboru kapitału lub skrajnej nieefektywności kosztowej. Wielokrotna iteracja metody Monte Carlo (n=10) dowiodła wysokiej stabilności (konwergencji) modelu mieszanego.

## Technologie

* R (pakiety: `fitdistrplus`, `MASS`)
* R Markdown
* Symulacja Monte Carlo
