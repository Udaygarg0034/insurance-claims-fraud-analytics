# Business insights

The following insights are calculated from the supplied 1,000-row dataset. They are descriptive findings, not evidence of causation.

## 1. Fraud exposure

- 247 of 1,000 claims are labelled fraudulent (`Y`).
- Overall fraud rate: **24.7%**.
- 753 claims are labelled non-fraud (`N`), or 75.3%.

## 2. Monthly claim volume and amount

| Month | Claims | Total claim amount | Average claim amount |
|---|---:|---:|---:|
| January 2015 | 516 | 27,760,970 | 53,800.33 |
| February 2015 | 472 | 24,326,250 | 51,538.67 |
| March 1, 2015 | 12 | 674,720 | 56,226.67 |

January has 44 more claims than February. The January and February trend visuals should exclude the 12 March records to match the assignment scope.

## 3. Fraud rate by incident type

| Incident type | Fraud rate |
|---|---:|
| Single Vehicle Collision | 29.0% |
| Multi-vehicle Collision | 27.2% |
| Parked Car | 9.5% |
| Vehicle Theft | 8.5% |

Single-vehicle and multi-vehicle collision claims have the highest observed fraud rates among the incident types in this dataset.

## 4. Fraud rate by policy type

| Policy type (`policy_csl`) | Fraud rate |
|---|---:|
| 250/500 | 26.2% |
| 100/300 | 25.8% |
| 500/1000 | 21.7% |

The 250/500 and 100/300 policy groups have higher observed fraud rates than the 500/1000 group. Segment sizes should be considered before making operational decisions.

## 5. Data quality opportunity

The `property_damage`, `police_report_available`, and `collision_type` fields contain 360, 343, and 178 `?` placeholders respectively. Improving completeness at claim intake could strengthen downstream analysis and investigation.

## Interpretation cautions

- The dataset does not specify a currency; amounts are shown without a currency symbol.
- A higher observed segment rate does not prove that a policy or incident type causes fraud.
- These results are based on this sample and should not be generalized without further validation.
