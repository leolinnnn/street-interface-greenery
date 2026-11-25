# Reproduction and validation

[← Overview](../README.md) · [Methods](IMPLEMENTATION.md) · [Input dictionary](../data/README.md)

## Environment and command

Python 3.12, with the dependency versions specified in
[requirements.txt](../requirements.txt). From the repository root:

```sh
python -m pip install -r requirements.txt
python run_analysis.py --output outputs/reproduction
```

The runner requires a new output directory and reads inputs relative to its own
repository root. No image downloads or model-weight downloads occur in this run.

## Outputs

The analysis writes new files to the chosen output directory and checks the
computed results against archived reference tables. Use a new directory for each run.

| Output | Content |
| --- | --- |
| `area_summary.csv` | Point-to-area interface aggregation |
| `model_summary.csv`, `model_coefficients_hc3.csv` | Main-model fit and HC3 coefficient intervals |
| `robustness_*.csv`, `point_model_*.csv` | Seven sensitivity models and the clustered point model |
| `model_vif.csv`, `model_predictions.csv`, `type_*.csv`, `interface_gvi_correlations.csv` | Diagnostics and descriptive comparisons |
| `verification.json` | PASS status, sample counts and checked model results |

Expected adjusted R²: **0.4876908 / 0.7097321**. The M2-I interface coefficient is
**5.5145202 percentage points per SD**, with HC3 95% CI **[2.2749648, 8.7540757]**.

For a compact main-model example, run `python examples/verify_bangna.py`.

```sh
python -m unittest discover -s tests -v
```

The small analytical tests are configured in [GitHub Actions](../.github/workflows/checks.yml).
The full numerical reproduction is available through its manual workflow trigger.
See [implementation and validation](IMPLEMENTATION.md) for verification scope.

## Validation

The full run compares all numerical fields in six archived tables
(`rtol=1e-8, atol=1e-9`): the two main models, seven sensitivity models and
the area-clustered point model. Five analytical tests cover image class
fractions, aggregation, HC3 inference, network geometry and POI diversity.

The archived tables in `reference/` are comparison targets. The runner computes
its results from `data/` before checking them. A mismatch raises an error.
`verification.json` records the settings and checked quantities.

The published numerical command and all existing tests passed after the
25 November 2026 reorganization. The external image/GIS workflows were not rerun.
Research interpretation and source restrictions remain in
[PROVENANCE.md](../PROVENANCE.md) and the [research record](RESEARCH_RECORD.md).
