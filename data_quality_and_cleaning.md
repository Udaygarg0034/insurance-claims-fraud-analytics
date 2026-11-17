# Data quality and cleaning notes

## Source profile

- Rows: **1,000**
- Columns: **39**
- Exact duplicate rows: **0**
- Incident dates: **1 January 2015 – 1 March 2015**
- Fraud labels: `Y` = 247; `N` = 753

## Recommended Power Query treatment

| Field(s) | Observed issue | Recommended treatment |
|---|---|---|
| `policy_bind_date`, `incident_date` | Imported as text in the raw CSV | Parse using the appropriate US date locale; set to Date type |
| `policy_number`, `insured_zip` | Numeric-looking identifiers | Keep as Text to preserve identifier semantics and leading zeros where applicable |
| `collision_type` | 178 values contain `?` | Replace `?` with `Unknown` |
| `property_damage` | 360 values contain `?` | Replace `?` with `Unknown` |
| `police_report_available` | 343 values contain `?` | Replace `?` with `Unknown` |
| `authorities_contacted` | 91 actual nulls | Keep null or explicitly label as `Unknown`; do not Fill Down |
| `umbrella_limit` | One value is -1,000,000 | Retain and flag for source verification; do not silently replace |
| `capital-loss` | Negative values occur | Retain; negative capital loss is not automatically an error |
| `policy_bind_date` vs `incident_date` | One binding date is later than incident date | Flag for review; do not delete the claim automatically |

## Data type guidance

- Dates: `policy_bind_date`, `incident_date` → Date.
- Whole number: counts, age, years/months as customer, claim components, claim amount, policy deductible, vehicle year, etc.
- Decimal number: `policy_annual_premium` (and monetary fields if fractional values are present).
- Text: category fields, policy identifiers, ZIP identifiers, `fraud_reported`.
- Keep `fraud_reported` as Text because the supplied values are `Y` and `N`.

## Validation checks

- No exact duplicate rows were found.
- `total_claim_amount` equals `injury_claim + property_claim + vehicle_claim` on all 1,000 rows.
- `fraud_reported` contains 247 `Y` records and 753 `N` records.
- January has 516 claims, February has 472, and 1 March 2015 has 12.

## Important scope note

The assignment brief asks for January and February trends, while the CSV includes 12 claims on 1 March. Retain all rows in the source/model. Filter the monthly trend visuals to January and February only. If the entire page is filtered to January and February, the total claims KPI should show 988, not 1,000.
