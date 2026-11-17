# Compact numerical check

[← Research and full analysis](../README.md)

Run these commands from the repository root.



```sh
python -m pip install -r requirements.txt
python examples/verify_bangna.py
```

Input: `data/bangna-areas.csv`, a nine-column extract of the existing 25-area table.
Types: A condominium, B house, C shophouse, D informal settlement. `gvi_pct` is
vegetation-only GVI in percent. `interface_openness_mean` is IO on a 0–100 scale;
larger values indicate greater interface openness. The original IO formula is
100 × (SET + VIS + (2 − VEH)) / 6, with each coded component in {0,1,2}.

The remaining predictors are mean network distance to Bang Na BTS (metres),
major-road share (fraction), and mean POI Shannon diversity in 400 m buffers.
`gvi_point_count` and `n_images` are sample counts. No property-price fields,
raw imagery or individual records are included.

The model uses shophouse (C) as the reference category, sample-SD standardization
(ddof=1), OLS, HC3 covariance and a t reference distribution with n − k degrees of
freedom. M2 has residential types and three spatial controls; M2-I adds IO.
Expected adjusted R²: 0.4876908 / 0.7097321. IO: 5.5145202 percentage points per SD,
95% CI [2.2749648, 8.7540757]. This is an association in 25 areas, not a causal estimate.

This compact script is newly prepared for the portfolio and independently recomputes
the stored main-model results. The research manuscript is by Zihao Lin and Lei Shao;
manuscript publication status and a separate Bang Na public data license are not
asserted here. Retain attribution; contact the authors for reuse beyond inspection.



The reference output is recorded in [expected-results.json](expected-results.json).
