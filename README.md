# 📈 Operational AI: Multi-Store Demand Forecasting Engine
### *Optimizing Retail Supply Chains with Gradient Boosting & Automated Time-Series Decomposition*

## 📝 Executive Summary
This project delivers an enterprise-grade forecasting engine evaluated on **1,100+ Rossmann pharmacies**. In retail operations, stockouts mean lost revenue, and overstocking locks up vital capital. By moving from simple averages to an optimized framework, I achieved a **Validation RMSPE of 17.24%** over a future 6-week operational horizon, enabling precise inventory procurement.

## 🚀 Architectural Benchmarking
I built and evaluated two distinct forecasting paradigms to balance global cross-store insights with local individual store patterns:

1. **The Machine Learning Approach (Tuned XGBoost):**
   * **Result:** 17.24% RMSPE (Deep tree structure with `max_depth=12`).
   * **Strength:** Mastered non-linear combinations of complex exogenous features (e.g., mapping how a `Promo` behaves dynamically depending on the `DayOfWeek`).
   
2. **The Statistical Component Approach (Meta Prophet):**
   * **Result:** 17.17% RMSPE (Isolated Store 1 Benchmarking).
   * **Strength:** Seamlessly isolated structural components—identifying a massive operational traffic surge every **Monday** and an exponential **+2,000 unit volume spike** during the holiday season.

## 💡 Key Senior-Level Engineering Decisions
* **Temporal Guardrails:** Avoided catastrophic data leakage by implementing a strict **chronological validation split**, training exclusively on past data and testing on the subsequent 6 weeks of the future.
* **Leakage Avoidance:** Purged the `Customers` feature from the training matrix. While highly correlated with sales, foot traffic cannot be known in advance, making it an invalid feature for production inference.
* **Domain-Specific Imputation:** Filled missing `CompetitionDistance` values with a macro-constant ($Max \times 2$) instead of the mean. This mathematically signals to the tree structures that the store operates in an unconstrained open market, avoiding suppressed sales forecasts.

## 🛠️ Tech Stack
* **Modeling:** XGBoost, Meta Prophet, Scikit-learn
* **Data Pipelines:** Pandas, NumPy
* **Visualization:** Seaborn, Matplotlib

## 📈 How to Run
1. Clone the repository.
2. Run `pip install -r requirements.txt`.
3. Execute `notebooks/demand_forecasting_benchmarking.ipynb` to visualize the demand curves and feature impacts.
