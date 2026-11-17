# Dashboard build guide

## Page 1 – Leadership Overview

### Header
- Title: **INSURANCE CLAIMS & FRAUD ANALYTICS**
- Subtitle: **Leadership Overview | Claims Performance | 2015**

### Slicers
Use dropdown slicers for:
- `Claim Month`
- `insured_sex`
- `policy_csl`
- `Fraud Status`

Keep slicers cleared when displaying full-dataset KPIs. A slicer selection should intentionally change the KPI values.

### KPI cards
Use these measures:
- `[Total Claims]`
- `[Total Claim Amount]`
- `[Average Claim Amount]`
- `[Fraud Percentage]`

Full-dataset reference values: 1,000; 52,761,940; 52,761.94; 24.70%.

### Visuals
- Clustered column: `Claim Month` by `[Total Claims]` (visual-level filter January and February).
- Line or column chart: `Claim Month` by `[Total Claim Amount]` (visual-level filter January and February).
- Donut: `Fraud Status` in Legend, `[Total Claims]` in Values.
- Bar chart: `policy_csl` by `[Fraud Percentage]`.
- Bar chart: `incident_type` by `[Fraud Percentage]`.

## Page 2 – Detailed Claims Analysis

Suggested visuals:
- Claims by `insured_education_level`.
- Average claim amount by `insured_sex`.
- Claims by `auto_make`.
- Average claim amount by `auto_year`.
- Claim amount by `policy_csl`.
- Claim count by `policy_csl`.

## Formatting recommendations

- Use a light neutral page background and white visual backgrounds.
- Use one primary blue for bars, navy for headings, and a restrained orange for fraud emphasis.
- Use consistent font sizes and chart titles.
- Align KPI cards and charts; avoid overlapping visuals and scrollbars.
- Keep chart labels readable and avoid unnecessary visual borders.

## Interactions

Test each slicer. Use **Format → Edit interactions** to ensure slicers filter the intended visuals. Keep the Month slicer and visual-level month filters conceptually distinct: the slicer is for user exploration; the Jan/Feb filter is for the assignment's trend charts.
