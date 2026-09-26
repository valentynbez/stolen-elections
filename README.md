# Forensic Electoral Analysis: The Shpilkin Method
## Cross-National Electoral Forensics: Russia, France, and Azerbaijan

Recreating, extending, and cross-validating the statistical electoral forensic methodology pioneered by **Sergey Shpilkin** ([Google Scholar Profile](https://scholar.google.com/citations?user=kX-Zzb4AAAAJ&hl=en)) and referenced at [deg.zhizhin.xyz/shpilkin.html](https://deg.zhizhin.xyz/shpilkin.html).

This repository contains reproducible data, statistical models, and fully annotated visualizations comparing **three distinct political systems**:
1. **Russia (State Duma Elections):** Competitive authoritarianism characterized by bimodal turnout distributions (*"Putin's Peaks"*), heavy ballot box stuffing, and regional "electoral sultanates".
2. **France 2022 (Presidential Election Round 2):** A **democratic baseline control** demonstrating unimodal Gaussian normality, near-zero turnout-share correlation, and complete absence of integer rounding artifacts.
3. **Azerbaijan 2020 (Parliamentary Elections):** A **hegemonic autocratic benchmark** characterized by administrative target-setting, severe multiples-of-5% integer rounding (*Sawtooth / Пила*), and turnout ceiling anomalies.

---

## 🔬 Academic Foundations & Literature

The analyses in this repository directly implement and validate the methodology published by **Sergey Shpilkin** and academic collaborators:

### Foundational Publications
1. **Statistical Fingerprints of Electoral Fraud:**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2016a). *Statistical fingerprints of electoral fraud?* **Significance**, 13(4), 20–23. [doi:10.1111/j.1740-9713.2016.00936.x](https://doi.org/10.1111/j.1740-9713.2016.00936.x)  
   *Establishes the unimodal Gaussian assumption for clean turnouts and the forensic signatures of vote fabrication.*

2. **The "Sawtooth" Integer Effect (*Пила*):**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2016b). *Integer percentages as electoral falsification fingerprints.* **The Annals of Applied Statistics**, 10(1), 54–73. [doi:10.1214/16-AOAS904](https://doi.org/10.1214/16-AOAS904)  
   *Mathematical proof that precinct clusters at exact integer percentages and multiples of 5% reflect human quota targeting rather than natural voter counts.*

3. **Turnout Distribution Distortions ("Putin's Peaks"):**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2018). *Putin's peaks: Russian election data revisited.* **Significance**, 15(3), 8–9. [doi:10.1111/j.1740-9713.2018.01141.x](https://doi.org/10.1111/j.1740-9713.2018.01141.x)  
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2020). *Suspect peaks in Russia's "referendum" results.* **Significance**, 17(5), 8–9. [doi:10.1111/1740-9713.01438](https://doi.org/10.1111/1740-9713.01438)  
   *Longitudinal documentation of bimodal turnout curves and fabricated high-turnout precincts.*

4. **2D Joint Distribution Correlation Analysis:**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2012). *Statistical anomalies in 2011–2012 Russian elections revealed by 2D correlation analysis.* **arXiv preprint arXiv:1205.0741**. [arxiv.org/abs/1205.0741](https://arxiv.org/abs/1205.0741)  
   *Bivariate Turnout vs. Vote Share diagnostics, ordinary least squares hypothesis testing ($H_0: b = 0$), and Gaussian mixture decomposition.*

5. **Substantive Regional Engineering:**
   > Kalinin, K., & Mebane, W. R. (2016). *When the Russian state engineer stipulates: Substantive and statistical characteristics of Russian electoral data.* **Russian Politics**, 1(2), 171–197.  
   *Demonstrates divergence between standard demographic regions and autocratic regional "sultanates".*

6. **Azerbaijani Electoral Forensics:**
   > Shpilkin, S. (2018). *Azerbaijani presidential elections 2018: What the numbers can tell us.* II Round Table of Mathematicians on Electoral Forensics, [Electoral.Graphics](https://electoral.graphics).  
   *Statistical analysis of precinct-level reporting and quota fabrication in Azerbaijan.*

---

## 📊 Cross-National Comparative Forensics Scorecard

| Forensic Metric / Diagnostic Test | France 2022 (Democratic Control) | Poland 2025 (Democratic Control) | Russia 2026 (Competitive Autocracy) | Azerbaijan 2020 (Hegemonic Autocracy) |
| :--- | :--- | :--- | :--- | :--- |
| **Analyzed Polling Stations (UIKs / Obwody)** | 64,650 | 31,653 | 83,798 | 5,571 |
| **Electorate Registered Voters** | 48,358,531 | 29,346,743 | 96,823,710 | 5,358,138 |
| **Official Turnout (%)** | 72.0% | 71.6% | 55.1% | 46.8% |
| **Leading / Regime Vote Share (%)** | 58.6% (Macron) | 50.9% (Nawrocki) | 56.6% (Regime) | 41.2% (YAP) |
| **OLS Regression Slope ($b$)** | **$-0.0636$** | **$-0.4879$** | **$+0.6348$** | **$+0.3949$** |
| **Pearson Correlation ($r$)** | **$-0.0413$** | **$-0.2624$** | **$+0.6533$** | **$+0.4133$** |
| **Coefficient of Determination ($R^2$)** | **$0.0017$** (Zero correlation) | **$0.0689$** (Demographic cleavage) | **$0.4267$** (Extreme correlation) | **$0.1708$** (Strong correlation) |
| **Turnout Distribution Modality** | Unimodal Normal (Peak: ~78%) | Unimodal Normal (Peak: ~72%) | Bimodal (Peaks: 43% and 75–100%) | Unimodal Skewed + 100% Spikes |
| **Near-Integer Precincts (% vs 10% expected)** | 10.24% (Matches uniform null) | 10.08% (Matches uniform null) | 11.85% (Significant excess, $z = 20.9$) | 10.81% (Statistically elevated, $z = 2.01$) |
| **Multiples of 5% Precincts (% vs 2% expected)** | 2.08% (Matches uniform null) | 2.23% (Matches uniform null) | 3.30% (Severe sawtooth spikes) | 2.75% ($4\sigma$ nationwide; **6.33% in tail $\ge 60\%$**) |
| **Turnout Ceiling Artifacts** | 0 precincts at 100% | 64 precincts (Hospitals/prisons) | 1,483 precincts at 100% | 37 precincts at 100% |
| **Forensic Diagnosis / Regime Typology** | **Statistically Independent & Organic** | **Competitive Democratic Mobilization** | **Dual-Electorate / Ballot Box Stuffing** | **Administrative Protocol Fabrication** |

---

## 🧭 Notebook Section Mapping

The primary analysis is executed in [`notebooks/stolen-elections.ipynb`](notebooks/stolen-elections.ipynb):

| Section | Focus / Methodology | Key Empirical Finding |
|---|---|---|
| **1. Data Ingestion & Features** | CIK protocols, remote electronic voting (DEG) tags | 87,842 Russian polling stations loaded and prepared |
| **2. Shpilkin Dual Histograms** | Kobak et al. (2016a, 2018) | Dual bimodal peaks: organic peak at ~43% vs. artificial "second hump" across 75%–100% |
| **3. Metric Variations (Vote Shares)** | Candidate share dynamics across turnout bins | Opposition shares collapse to ~0% while regime candidate surges toward ~95% |
| **4. Remote Electronic Voting (DEG)** | Centralized multiplier analysis | 97 DEG pseudo-stations cluster at extreme 85%–95% turnout with near-total regime margin |
| **5. Precinct-Level OLS Regression** | Kobak et al. (2012) bivariate regression | $\text{Share} = 17.4 + 0.603 \times \text{Turnout}$ ($r = 0.624, R^2 = 0.390, p < 0.0001$), rejecting $H_0: b = 0$ |
| **6. Gaussian Mixture Models (EM)** | 2-component unsupervised clustering | Partitions electorate: Organic Cluster (49.3% wt, turnout 45.0%) vs. Anomalous Cluster (50.7% wt, turnout 77.0%) |
| **7. The Sawtooth Rounding Effect** | Kobak et al. (2016b, *AOAS*) | Pronounced spikes at exact multiples of 5% (70%, 75%, 80%, 85%, 90%, 95%, 100%) |
| **8. Shpilkin Excess Votes Model** | Non-parametric anomaly subtraction | **14.6M anomalous votes** in Party List (45.4% of UR paper total); **12.9M** in Single-Mandate |
| **9. Regional Contrasts** | Kalinin & Mebane (2016) | Standard bell curves (Tomsk, Khabarovsk) vs. "electoral sultanates" with uniform 95% turnout (Kuzbass, Tatarstan) |
| **10. International Democratic Baseline** | France 2022 Presidential Control (69k stations) | Flat slope ($b = -0.064$), Gaussian curve, and zero integer rounding artifacts |
| **11. Autocratic Forensics (Azerbaijan)** | 2020 Parliamentary Elections (5,571 stations) | Strong positive slope ($b = +0.395, r = +0.413$), $10\sigma$ spikes at 5% multiples in high-turnout tail, and 37 precincts at 100% |
| **12. Central European Control (Poland)** | 2025 Presidential Runoff (32k stations) | Negative conservative slope ($b = -0.488$), positive liberal slope ($b = +0.488$), 71.6% organic turnout, and zero rounding spikes |
| **13. Cross-National Conclusions** | Triangulated 4-way comparative synthesis | Definitive statistical validation of electoral manipulation typologies across democratic and autocratic regimes |

---

## 📁 Repository Structure

```
├── data/
│   ├── uik_protocols.csv.gz              # Consolidated Russian CIK protocol data (87,842 UIKs)
│   ├── france_2022_t1_clean.csv.gz       # French 2022 Presidential Round 1 cleaned (69,682 bureaux)
│   ├── france_2022_t2_clean.csv.gz       # French 2022 Presidential Round 2 cleaned (Macron vs Le Pen)
│   ├── poland_2025_t1_clean.csv.gz       # Polish 2025 Presidential Round 1 cleaned (32,143 obwody)
│   ├── poland_2025_t2_clean.csv.gz       # Polish 2025 Presidential Round 2 cleaned (Nawrocki vs Trzaskowski)
│   ├── poland_2025_protocols_t1_raw.zip  # Official raw PKW protocol export for Round 1
│   ├── poland_2025_protocols_t2_raw.zip  # Official raw PKW protocol export for Round 2
│   ├── azerbaijan_2020_mm_clean.csv.gz   # Azerbaijan 2020 Parliamentary cleaned (5,571 məntəqə)
│   ├── azerbaijan_parliament_2020.zip    # Raw Electoral.Graphics / EMDS Excel dataset
│   └── azerbaijan_cec_protocols_2020.zip # Official CEC PDF protocols archive
├── notebooks/
│   └── stolen-elections.ipynb            # Fully executed 34-cell Jupyter Notebook with figures
├── writeups/
│   └── blogpost.MD                       # Markdown writeup and article draft
├── README.md
└── .gitignore
```

---

## 🚀 Getting Started

### Prerequisites

Create a conda environment or virtual environment with the required dependencies:

```bash
conda create -n data-analysis python=3.12 -y
conda activate data-analysis
conda install pandas numpy matplotlib scipy scikit-learn seaborn statsmodels jupyter openpyxl -y
```

### Running the Notebook

```bash
jupyter notebook notebooks/stolen-elections.ipynb
```

---

## 📚 Acknowledgments & Data Sources

- **Methodology & Foundations:** Sergey Shpilkin, Dmitry Kobak, Maxim S. Pshenichnikov, Walter R. Mebane, Kirill Kalinin.
- **Russian Electoral Protocols:** CIK (izbirkom.ru) protocols, mirrored by [iditena.org](https://iditena.org), [neshodilina.netlify.app](https://neshodilina.netlify.app), and [data.deg.observer](https://data.deg.observer).
- **French Democratic Control Data:** Ministère de l'Intérieur / data.gouv.fr (*Élection présidentielle 2022: résultats par bureaux de vote*).
- **Polish Democratic Control Data:** National Electoral Commission of Poland / Państwowa Komisja Wyborcza (*Wybory Prezydenta Rzeczypospolitej Polskiej 2025: protokoły po obwodach* via `prezydent2025.pkw.gov.pl`).
- **Azerbaijan Electoral Data:** Central Election Commission of the Republic of Azerbaijan (*Mərkəzi Seçki Komissiyası*), Election Monitoring and Democracy Studies Center (EMDS), and [Electoral.Graphics](https://electoral.graphics).
