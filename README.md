# Multi-criteria evaluation of competing offers in U.S. residential real estate

Analysis code and supporting data for the study *A deployed multi-criteria decision model for evaluating competing offers in United States residential real estate*
(submitted to the Journal of Multi-Criteria Decision Analysis).

The study ranks five competing offers on a single residential listing across six criteria
using the Analytic Hierarchy Process, cross-checks the ranking against TOPSIS using the same
priorities, and tests robustness through an ablation study, a perturbation-based sensitivity
analysis and a comparison of two cost-to-benefit normalisation schemes.

## Contents

```
data/
  offers.csv                      five competing offers, one row per offer
  offers.json                     the same records in their original nested form
  criteria_definitions.csv        the six criteria, direction, units, normalisation
  pairwise_matrix.csv             6x6 judgement matrix on Saaty's fundamental scale
  survey_questions.csv            practitioner questionnaire instrument
  survey_responses.csv            three anonymised practitioner responses
  supporting_dataset.xlsx         all of the above as one workbook
  DATA_DICTIONARY.md              field-level documentation and model parameters
notebooks/
  AHP_offer_evaluation.ipynb      full analysis, reproduces every table and figure
figures/                          fig1 is the drawn hierarchy diagram; fig2 to fig6 and figS1 are
                                  written by the notebook, numbered as in the manuscript
```

## Source repository

https://github.com/pushparajbhatta/offer-evaluation-mcda

## Reproducing the analysis

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab notebooks/AHP_offer_evaluation.ipynb
```

Run all cells from inside `notebooks/`. Figures are written to `figures/` at 300 dpi.

## Key results

| Quantity | Value |
| --- | --- |
| Principal eigenvalue | 6.2578 |
| Consistency index | 0.0516 |
| Consistency ratio | 0.0416 |
| Priorities | NP 0.4615, CoC 0.2402, TF 0.1095, CR 0.1095, SEI 0.0515, IPF 0.0279 |
| AHP ranks (Offers 1 to 5) | 4, 3, 5, 2, 1 |
| TOPSIS ranks (Offers 1 to 5) | 4, 3, 5, 1, 2 |
| Spearman, AHP against TOPSIS | 0.900 |
| Rank shifts under 30 perturbations (ratio / linear) | 0 / 14 |

## Data provenance

Offer records were supplied by the operating platform under a research permission agreement
with personally identifying information removed. See `data/DATA_DICTIONARY.md`.

## How to cite

Bhatta, P. R., & Shakya, M. (2026). Multi-criteria evaluation of competing offers in U.S. residential real estate: analysis code and supporting data (Version 1.0) [Data set and software]. Zenodo. https://doi.org/10.5281/zenodo.23465853

## Licence

Code is released under the MIT Licence. Data and documentation are released under
Creative Commons Attribution 4.0 International (CC BY 4.0).
