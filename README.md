# Ovela MMM — Marketing Mix Modeling Portfolio Project

A end-to-end marketing measurement project for **Ovela**, a fictional DTC fertility 
supplement brand. Built to demonstrate practical ownership of a marketing mix modeling 
and measurement framework: from problem definition through regression modeling, 
attribution comparison, budget optimization, and executive communication.

---

## The business problem

Ovela runs paid media across Meta, Google, TikTok, email, and influencer. Like most 
DTC brands, its reporting stack relies on last-touch attribution — which overstates 
Meta performance, ignores view-through assists, and breaks down after iOS privacy 
changes. Leadership can't confidently answer: *which channels are actually driving 
revenue, and where should we shift budget?*

This project builds a measurement framework to answer that question.

---

## What I built

| Phase | Deliverable |
|---|---|
| 1 — Problem framing | Measurement brief: goals, constraints, model use cases |
| 2 — Dataset | Simulated 2-year weekly dataset with realistic channel dynamics |
| 3 — MMM | Regression model with adstock, saturation curves, contribution decomp |
| 4 — Attribution comparison | Last-touch vs MMM vs holdout logic — where they agree and disagree |
| 5 — Budget optimizer | Scenario tool using MMM response curves to maximize projected revenue |
| 6 — Executive narrative | 6-slide deck with findings, recommendations, and honest limitations |

---

## Key findings (simulated)

- **Paid search** showed the strongest incremental contribution per dollar — 
  underweighted in last-touch due to assist misattribution to Meta
- **Meta** was overvalued by ~35% in last-touch vs MMM contribution
- **TikTok** showed high saturation at current spend — marginal returns declining 
  past ~$15K/week
- **Recommended reallocation**: shift 20% of Meta budget to paid search + email, 
  projected +8–12% revenue lift on flat total spend

---

## Tech stack

- **Python** — pandas, numpy, statsmodels, scikit-learn, matplotlib, seaborn
- **SQL** — schema design, staging and mart transformations (DuckDB / BigQuery style)
- **Jupyter notebooks** — one per phase, narrative-driven
- **Excel/Sheets** — budget scenario output for stakeholder use

---

## Repo structure

```
ovela-mmm/
├── data/
│   ├── raw/                  # Simulated weekly CSVs
│   └── processed/            # Transformed model inputs
├── sql/
│   └── schema.sql            # Staging + mart definitions
├── notebooks/
│   ├── 01_data_generation.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_mmm_model.ipynb
│   ├── 04_attribution_comparison.ipynb
│   └── 05_budget_optimizer.ipynb
├── src/
│   ├── adstock.py
│   ├── saturation.py
│   └── optimizer.py
├── outputs/
│   └── charts/
├── deck/
└── requirements.txt
```


---

## How to run

```bash
git clone https://github.com/YOUR_USERNAME/ovela-mmm.git
cd ovela-mmm
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Open notebooks in order, starting with `01_data_generation.ipynb`.

---

## Limitations and next steps

This is a starter MMM, not a production model. Known limitations:

- Adstock decay rates are assumed, not validated against holdout experiments
- Influencer channel lacks impression-level data — contribution is likely understated
- Model requires recalibration every 6–12 months as brand scales and mix shifts
- A Bayesian extension (e.g. Robyn or PyMC-Marketing) would add uncertainty 
  quantification around coefficient estimates

**Next steps if this were a live brand:** run a geo holdout test on paid search to 
validate MMM coefficients, instrument TikTok with pixel + modeled conversions, 
and build a lightweight recalibration cadence tied to quarterly planning.

---

## About this project

Built as a portfolio project to demonstrate practical marketing measurement skills — 
not positioning as a Bayesian MMM specialist, but as someone who can own the full 
measurement workflow: define the problem, build the model, challenge it with 
attribution logic, and translate it into budget decisions an exec can act on.
