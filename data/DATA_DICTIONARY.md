# Data dictionary

All monetary amounts are in United States dollars. Dates follow ISO 8601 (YYYY-MM-DD).
Boolean-like fields use the strings `yes` and `no` as captured by the platform form.

## offers.csv

Five competing offers on a single residential listing. One row per offer.

| Field | Type | Description |
| --- | --- | --- |
| `offer_id` | integer | Sequential identifier within this offer set. Not a platform key. |
| `offer_price` | integer | Headline price offered by the buyer. |
| `earnest_money` | integer | Deposit committed by the buyer at contract. |
| `proposed_closing_date` | date | Closing date proposed in the offer. |
| `immediate_possession` | string | Whether the offer accommodates immediate possession. |
| `discount_amount` | integer | Price reduction applied against the headline offer price. |
| `buyer_agent_commission_paid_by_seller` | string | Whether the seller is asked to pay the buyer agent commission. |
| `buyer_agent_commission_amount` | integer | Amount of that commission. |
| `buyer_closing_cost_paid_by_seller` | string | Whether the seller is asked to pay buyer closing costs. |
| `buyer_closing_cost_amount` | integer | Amount of those closing costs. |
| `down_payment_assistance_paid_by_seller` | string | Whether the seller is asked to contribute to the down payment. |
| `down_payment_assistance_amount` | integer | Amount of that contribution. |
| `additional_assistance_required_by_buyer` | string | Whether further buyer assistance is requested. |
| `additional_assistance_amount` | integer | Amount of that assistance. |
| `repairs_paid_by_seller` | string | Whether the seller is asked to pay for repairs. |
| `repairs_amount` | integer | Value of those repairs. |
| `replacement_items_paid_by_seller` | string | Whether the seller is asked to pay for replacement items. |
| `replacement_items_amount` | integer | Value of those replacements. |
| `other_requests_requested_by_buyer` | string | Whether other buyer requests carry a cost. |
| `other_requests_amount` | integer | Value of those requests. |
| `inspection_requested` | string | Whether the buyer reserves an inspection period. |
| `inspection_days` | integer | Length of the inspection period in days. |
| `all_cash` | string | Whether the offer is all cash. |
| `bank_loan_amount` | integer | Loan amount where financing is used. |
| `down_payment_to_bank` | integer | Buyer down payment against the loan. |
| `other_financing` | string | Alternative financing instrument, where applicable. |
| `sale_contingent_on_other_property` | string | Whether completion depends on the buyer selling another property. |
| `property_tax_payment` | string | Agreed apportionment of property tax at closing. |

## criteria_definitions.csv

The six evaluation criteria, their direction (benefit or cost), units and the
transformation applied to put each on a common 0 to 1 scale where higher is better.

| Field | Description |
| --- | --- |
| `code` | Short code used throughout the analysis |
| `name` | Full criterion name |
| `direction` | Benefit (higher raw value preferred) or Cost (lower raw value preferred) |
| `definition` | How the criterion is computed from the offer record |
| `unit` | Unit of the raw value before normalisation |
| `normalisation` | Transformation applied to reach the 0 to 1 scale |

## pairwise_matrix.csv

The 6x6 judgement matrix on Saaty’s fundamental scale, elicited from a single decision
maker and reviewed with a domain expert. Row criterion compared against column criterion.
Reciprocal entries are stored explicitly as decimals rounded to six places.
Derived priorities: NP 0.4615, CoC 0.2402, TF 0.1095, CR 0.1095, SEI 0.0515, IPF 0.0279.
Principal eigenvalue 6.2578, consistency index 0.0516, consistency ratio 0.0416.

## survey_questions.csv and survey_responses.csv

The practitioner questionnaire and three anonymised responses, collected 22 January 2026.
Respondent identifiers R1 to R3 replace names. Role is retained in the first response column
because it is reported in the manuscript. Multiple-selection answers are semicolon separated.

## Parameters set outside the data files

| Parameter | Value | Where used |
| --- | --- | --- |
| Seller preferred closing date | 2025-10-25 | Timeline Fit |
| Timeline Fit decay window | 30 days | Timeline Fit |
| Inspection day monetary equivalent | 1000 USD per day | Contingency Risk |
| Certainty of Close score map | cash 1.0, loan 0.8, contract for deed 0.6, other 0.5 | Certainty of Close |
| Sensitivity perturbation | plus and minus 10 per cent on each judgement | Sensitivity analysis |
| Random index for n = 6 | 1.24 | Consistency ratio |

## Privacy

Offer records were supplied by the operating platform under a research permission agreement
with personally identifying information removed. No buyer name, agent name, contact detail,
property address or platform listing identifier appears in any field. Offer identifiers are
sequential within this set and do not correspond to platform keys.
