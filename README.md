# Customer Value Forecasting · RFM & Random Forest

A customer-value modeling exercise using **800 synthetic transactions** with an Olist-inspired schema. It engineers customer features from an initial observation window and compares a heuristic spending estimate with random forest regression.

## Workflow

1. Simulate transactions and inject missing payments and an outlier.
2. Clean payments and cap extreme values.
3. Split transactions into an initial 180-day window and a following 90-day revenue window.
4. Aggregate frequency, recency, average payment, and customer tenure.
5. Compare a hand-written heuristic with a random forest (200 trees, maximum depth 5).
6. Inspect MAE, MSE, RMSE, and prediction plots.

## Reading the results correctly

The notebook uses simulated data, not downloaded Olist marketplace data. The section labeled BG/NBD + Gamma-Gamma uses hand-written formulas; it does **not** fit either probabilistic model.

The random forest is trained on a customer subset but the displayed metrics are computed across **all customers**, including training customers. Those values are descriptive mixed-sample errors, not a clean estimate of generalization. The target is 90-day spending rather than an unrestricted lifetime value.

## Next improvements

- Fit preprocessing thresholds on the observation/training period only.
- Report regression metrics on held-out customers only, alongside a simple baseline.
- Fit actual BG/NBD and Gamma-Gamma models if a probabilistic comparison is required.
- Validate on appropriately licensed transaction data before drawing business conclusions.

## Open the project

- [Analysis notebook](part3.ipynb)
- [Presentation](Part3_CLTV%20(1).pptx)

## Run locally

Use Python 3 in an isolated environment:

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab
```

Open the notebook and run all cells from top to bottom. Data is generated inside the notebook; no external dataset download is required.

Dependencies are listed without exact version pins; results may vary slightly across library versions.
