# Forensic Electoral Analysis: The Shpilkin Method (Russian State Duma Elections)

Recreating and expanding upon the statistical electoral forensic analysis from [deg.zhizhin.xyz/shpilkin.html](https://deg.zhizhin.xyz/shpilkin.html).

This repository contains data, notebooks, and statistical models applying **Sergey Shpilkin's method** to analyze election protocols across 87,842 polling stations (UIKs) from the Russian State Duma elections.

---

## 🔬 Academic Foundations & References

The analyses in this repository directly implement and validate the methodology published by independent statistician **Sergey Shpilkin** ([Google Scholar Profile](https://scholar.google.com/citations?user=kX-Zzb4AAAAJ&hl=en)) and his co-authors:

### Key Publications
1. **Statistical Fingerprints of Electoral Fraud:**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2016a). *Statistical fingerprints of electoral fraud?* **Significance**, 13(4), 20–23. [doi:10.1111/j.1740-9713.2016.00936.x](https://doi.org/10.1111/j.1740-9713.2016.00936.x)  
   *Foundational framework establishing unimodal Gaussian turnout assumptions and the forensic signatures of manipulation.*

2. **The "Sawtooth" Integer Effect (*Пила*):**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2016b). *Integer percentages as electoral falsification fingerprints.* **The Annals of Applied Statistics**, 10(1), 54–73. [doi:10.1214/16-AOAS904](https://doi.org/10.1214/16-AOAS904)  
   *Mathematical proof that spikes at integer percentages and multiples of 5% in precinct protocols reflect human quota targeting rather than legitimate voting distributions.*

3. **Turnout Distribution Peaks ("Putin's Peaks"):**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2018). *Putin's peaks: Russian election data revisited.* **Significance**, 15(3), 8–9. [doi:10.1111/j.1740-9713.2018.01141.x](https://doi.org/10.1111/j.1740-9713.2018.01141.x)  
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2020). *Suspect peaks in Russia's "referendum" results.* **Significance**, 17(5), 8–9. [doi:10.1111/1740-9713.01438](https://doi.org/10.1111/1740-9713.01438)  
   *Longitudinal documentation of bimodal turnout distortions and anomalous high-turnout peaks.*

4. **2D Joint Distribution Correlation Analysis:**
   > Kobak, D., Shpilkin, S., & Pshenichnikov, M. S. (2012). *Statistical anomalies in 2011–2012 Russian elections revealed by 2D correlation analysis.* **arXiv preprint arXiv:1205.0741**. [arxiv.org/abs/1205.0741](https://arxiv.org/abs/1205.0741)  
   *Bivariate Turnout vs. Vote Share diagnostics, ordinary least squares hypothesis testing ($H_0: b = 0$), and Gaussian mixture decomposition.*

---

## 📊 Key Forensic Findings (Section Mapping)

| Analysis Section in Notebook | Academic Reference | Key Empirical Finding |
|---|---|---|
| **Section 2: Classic Shpilkin Histograms** | Kobak et al. (2016a, 2018) | Severe bimodal split: organic peak at ~43% turnout vs. artificial "second hump" across 75%–100% |
| **Section 3: Metric Variations (Vote Share)** | Kobak et al. (2016a) | Opposition shares collapse to ~0% as turnout rises, while regime candidate surges toward ~95% |
| **Section 4: Remote Electronic Voting (DEG)** | Shpilkin (2021/2026) | 97 DEG pseudo-stations cluster at extreme 85%–95% turnout with near-total regime margin |
| **Section 5: Precinct-Level OLS Regression** | Kobak et al. (2012) | $\text{Share} = 17.41 + 0.603 \times \text{Turnout}$ ($r = 0.624, R^2 = 0.390, p < 0.0001$), rejecting $H_0: b = 0$ |
| **Section 6: Gaussian Mixture Modeling (GMM)** | Kobak et al. (2012) | Objective EM separation: Organic Cluster (49.3% wt, turnout 45.0%) vs. Anomalous Cluster (50.7% wt, turnout 77.0%) |
| **Section 7: The Sawtooth Rounding Effect** | Kobak et al. (2016b, *AOAS*) | Pronounced spikes in precinct frequency at exact multiples of 5% (70%, 75%, 80%, 85%, 90%, 95%, 100%) |
| **Section 8: Shpilkin Excess Votes Model** | Shpilkin (2011/2012) | **14.6M anomalous votes** in Party List (45.4% of United Russia paper total); **12.9M** in Single-Mandate |
| **Section 9: Regional Contrasts** | Kalinin & Mebane (2016) | Standard bell curves (Tomsk, Khabarovsk) vs. "electoral sultanates" with uniform 95% turnout (Kuzbass, Tatarstan) |

---

## 📁 Repository Structure

```
├── data/
│   └── uik_protocols.csv.gz     # Consolidated CIK protocol data (87,842 UIKs)
├── notebooks/
│   └── stolen-elections.ipynb   # Fully executed Jupyter Notebook with charts and English annotations
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
conda install pandas numpy matplotlib scipy scikit-learn seaborn statsmodels jupyter -y
```

### Running the Notebook

```bash
jupyter notebook notebooks/stolen-elections.ipynb
```

---

## 📚 Acknowledgments & Attribution

- **Methodology & Concept:** Sergey Shpilkin, Dmitry Kobak, Maxim S. Pshenichnikov
- **Interactive Platform Reference:** [deg.zhizhin.xyz/shpilkin.html](https://deg.zhizhin.xyz/shpilkin.html)
- **Data Integration:** Official CIK (izbirkom.ru) protocols, mirrored and archived by [iditena.org](https://iditena.org), [neshodilina.netlify.app](https://neshodilina.netlify.app), and [data.deg.observer](https://data.deg.observer).
