
---

### 📍 Overview

In this project, we designed a stock portfolio that **minimizes Conditional Value-at-Risk (CVaR)**, a robust measure of tail risk, using **linear programming and daily returns from 100 Nasdaq stocks**. The portfolio was optimized on **2019 data (pre-COVID)** and evaluated out-of-sample on **2020 data (COVID onset)** to assess real-world resilience.

We tested sensitivity to **confidence level (β)**, experimented with **alternative CVaR formulations**, and introduced **dynamic monthly rebalancing** and **portfolio stability constraints**.

---

### 🎯 Project Goals

- Minimize CVaR at multiple confidence levels (β = 0.90, 0.95, 0.99)
- Analyze **in-sample vs. out-of-sample CVaR** to quantify generalization error
- Compare static vs. dynamic allocation strategies
- Implement **min-max CVaR optimization** to guard against worst-month losses
- Evaluate the cost-benefit of **rebalancing and stability constraints**

---

### 🧠 Optimization & Data Science Methods Used

| Area | Tools & Techniques Applied |
| --- | --- |
| **Risk Modeling** | Conditional Value-at-Risk (CVaR), Value-at-Risk (VaR), Min-Max CVaR formulation |
| **Optimization Engine** | Linear programming using **Gurobi** |
| **Model Constraints** | Return floor constraint, budget constraint, weight sum = 1, stability bounds |
| **Scenario Modeling** | Sample-based CVaR estimation with historical returns |
| **Backtesting** | Out-of-sample testing on 2020 pandemic returns |
| **Sensitivity Analysis** | Varying confidence level β and observing resulting portfolio allocations |
| **Rolling Rebalancing** | Monthly re-optimization using 12-month trailing window |
| **Portfolio Stability** | Enforced max ±5% month-to-month change in weight per asset |

---

### 📊 Key Findings

### ✅ Base Case Portfolio (β = 0.95)

- **In-Sample CVaR (2019):** 0.0111
- **Out-of-Sample CVaR (2020):** 0.0466
- Outperformed Nasdaq index (NDX CVaR: 0.0565) in both years
- Concentrated in **defensive stocks** like XEL (Utilities) and CHTR (Communications)

### 📈 Sensitivity to β (Confidence Level)

- As β increases (from 0.90 → 0.99), portfolio becomes **more conservative**
- CVaR rises, and allocations shift towards **lower volatility sectors**
- At β = 0.99, XEL comprised **45% of portfolio**

### ⚠️ Alternative Objective – Min-Max CVaR

- Reduced **worst-case monthly tail risk** (CVaR max = 0.013 vs. 0.016 in base)
- Outperformed NDX again, with improved **CVaR consistency** across months

---

### 🔁 Dynamic Rebalancing (Rolling Optimization)

We implemented a **monthly rebalancing strategy**, where each month's portfolio is trained on the prior 12 months.

**Benefits Observed**:

- Lower average CVaR in 2020 vs. static 2019 allocation
- Better responsiveness to **market shocks** like the COVID crash in March 2020
- Exposed volatility of tail risk over time

---

### 📉 Portfolio Stability Analysis

- Found large, impractical **weight swings >5%** month to month
- Introduced **±5% stability constraint** on allocations in the model
- Reduced turnover while maintaining acceptable CVaR performance
- Balance struck between **risk control and operational feasibility**

---

### 📚 Skills Gained

| Category | Skills |
| --- | --- |
| **Modeling** | Convex risk minimization, tail risk estimation, linear programming |
| **Tools** | Python, Gurobi, NumPy, pandas, Matplotlib |
| **Quantitative Thinking** | CVaR theory, overfitting avoidance, generalization testing |
| **Finance Insight** | Tradeoff between diversification, risk aversion, and rebalancing cost |
| **Communication** | Built interactive visualizations and delivered clear write-up of results |

---

### 💡 Takeaways

- **CVaR is a more robust risk measure** than VaR in turbulent markets
- **Static portfolios overfit** and fail out-of-sample; **dynamic rebalancing improves resilience**
- **Stability constraints are necessary** for real-world implementation
- Tail risk is dynamic — models must be updated regularly to stay effective

---
