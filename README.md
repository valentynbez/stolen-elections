# Forensic Electoral Analysis: The Shpilkin Method (Russian State Duma Elections)

Recreating and expanding upon the statistical electoral forensic analysis from [deg.zhizhin.xyz/shpilkin.html](https://deg.zhizhin.xyz/shpilkin.html).

This repository contains data, notebooks, and statistical models applying **Sergey Shpilkin's method** to analyze election protocols across 87,842 polling stations (UIKs) from the Russian State Duma elections.

---

## 📊 Key Forensic Findings

1. **Massive Bimodal Distribution ("The Second Hump"):**
   - The genuine electorate forms a standard bell curve centered around **~42%–45% modal turnout**.
   - An artificial second peak extends across **75% to 100% turnout**, where incremental votes are allocated almost exclusively to the ruling party (*United Russia* / administrative incumbent), while opposition candidate totals collapse toward zero.

2. **Quantification of Fabricated / "Stolen" Ballots (Shpilkin Model):**
   - **Federal Party List:** An estimated **14.6 million anomalous votes** (45.4% of United Russia's official paper ballots). Removing these excess votes drops estimated United Russia paper support from **58.7% to ~43.7%**, and national paper turnout from **55.5% to ~47.8%**.
   - **Single-Mandate Districts:** An estimated **12.9 million anomalous votes** (43.5% of official regime votes), lowering estimated support from **55.3% to ~41.1%**.

3. **Turnout vs. Candidate Share Divergence (OLS Regression):**
   - Ordinary Least Squares regression on $N = 87,700+$ paper polling stations:
     $$\text{Vote Share} = 17.41 + 0.6030 \times \text{Turnout} \quad (r = 0.624, \; R^2 = 0.390, \; p < 0.0001)$$
   - Rejects the null hypothesis of unmanipulated voting ($H_0: b = 0$).

4. **Gaussian Mixture Modeling (EM Decomposition, 2 Components):**
   - **Cluster 1 (Baseline / Organic Electorate, 49.3% weight):** Mean Turnout $45.0\% \pm 12.1\%$, Mean Vote Share $42.1\% \pm 16.0\%$.
   - **Cluster 2 (Anomalous / Manipulated Electorate, 50.7% weight):** Mean Turnout $77.0\% \pm 13.2\%$, Mean Vote Share $66.2\% \pm 15.3\%$.

5. **Remote Electronic Voting (DEG / ДЭГ):**
   - Analyzes the **33 regions** with DEG vs. **56 regions** without DEG.
   - The 97 electronic pseudo-stations (`is_deg == 1`) cluster at extreme turnouts (**85%–95%**) with near-total regime margins.

6. **The "Sawtooth" Integer Effect (*Пила*):**
   - Significant artificial spikes in precinct turnout counts at exact multiples of 5% and 10% (70%, 75%, 80%, 85%, 90%, 95%, 100%), characteristic of protocol target fabrication.

---

## 📁 Repository Structure

```
├── data/
│   └── uik_protocols.csv.gz     # Consolidated CIK protocol data (87,842 UIKs)
├── notebooks/
│   └── stolen-elections.ipynb   # Executed Jupyter Notebook with charts and English annotations
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

## 📚 Acknowledgments & References

- **Methodology:** Sergey Shpilkin
- **Analysis Reference:** [deg.zhizhin.xyz/shpilkin.html](https://deg.zhizhin.xyz/shpilkin.html)
- **Data Integration:** Official CIK (izbirkom.ru) protocols, mirrored and archived by [iditena.org](https://iditena.org), [neshodilina.netlify.app](https://neshodilina.netlify.app), and [data.deg.observer](https://data.deg.observer).
