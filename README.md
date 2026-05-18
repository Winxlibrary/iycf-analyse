IYCF Analyse Application – Release Notes
Release Version: v1.0
Release Type: Initial Stable Release
Platform: Windows (Flutter Desktop)
Date: May 2026

🍼 Overview
The IYCF Analyse Application is a desktop tool designed to import, validate, and analyse Infant and Young Child Feeding (IYCF) survey data.
It supports logic‑aware validation, unweighted and weighted indicator computation, and professional-quality outputs aligned with WHO, UNICEF, DHS, and SMART methodologies.
This release focuses on data quality assurance, robust indicator computation, and clear reporting workflows for field teams and analysts.

✅ Key Features
1. Excel Import & Template Validation

Imports IYCF data from a dedicated “IYCF” Excel sheet
Enforces strict template structure:

Required core columns (ID, Cluster, Team, Sex, Interview Date, Birth Date, etc.)
Mandatory Weight and Strata headers


Automatically rejects incorrect or malformed templates with clear feedback


2. Logic‑Aware Data Validation

Implements skip‑logic consistent with IYCF questionnaires

Questions are only validated when applicable
Non‑applicable (NA) fields are not treated as errors


Differentiates between:

Errors → invalidate rows and exclude them from analysis
Warnings → flag unusual or defaulted values without excluding rows


Examples:

Missing frequency where parent response is “No” → allowed
Missing weight or strata → defaulted safely to 1 with warning
Invalid codes in required fields → flagged as errors




3. Weight & Strata Handling

Supports optional survey design variables:

Weight (default = 1.0 when missing)
Strata (default = “1” when missing)


Defaults are applied per row, not globally
Both fields are tracked in metadata and outputs for transparency


4. Indicator Computation

Computes core IYCF indicators, including:

Early Initiation of Breastfeeding (EIBF)
Exclusive Breastfeeding (0–5 months)
Mixed Milk Feeding
Continued Breastfeeding (12–23 months)
Minimum Dietary Diversity (MDD)
Minimum Meal Frequency (MMF)
Minimum Acceptable Diet (MAD)
Bottle Feeding, Sweet Beverage consumption, etc.


Indicators correctly exclude non‑applicable cases from denominators
NA values never artificially inflate or deflate results


5. Weighted & Design‑Based Analysis (Advanced)

Supports clustered, stratified survey analysis
Implements:

Weighted proportions
PSU‑based Taylor linearization variance
Design Effect (DEFF)
Kish effective sample size


Outputs design‑adjusted 95% confidence intervals
Generates DHS‑style long‑format tables for reporting


6. Data Quality Issue Export (New)
A dedicated Data Issues Export has been added to support rapid data cleaning.
When users select “Export data issues (.xlsx)”, the app generates an Excel file with:
📄 Sheet 1: Issues_Summary

Total imported rows
Invalid rows (excluded from analysis)
Valid rows with warnings
Top recurring error messages
Top recurring warning messages

📄 Sheet 2: Invalid_Rows

Row number
ID
Cluster, Team, Household
Sex, Age (months), Age group
Detailed error messages

📄 Sheet 3: Warnings

Row number
ID
Cluster, Team, Household
Sex, Age (months), Age group
Detailed warning messages

This enables supervisors and field teams to quickly identify, filter, and correct data problems before re‑analysis.

7. Reporting & Export

Generates:

Analysed Excel reports with summary tables
Disaggregated indicator tables (by sex, cluster, team, strata)
Dashboard‑ready CSV outputs
DHS‑style weighted CSV outputs


Includes Wilson confidence intervals for unweighted analyses
Flags small denominators to prevent misinterpretation


8. Interactive Data Review

Built‑in spreadsheet‑style viewer:

Filter by All / Warnings / Invalid
Search by ID, cluster, team, age, errors, or warnings


Visual cues:

✅ Green → Valid
⚠️ Orange → Warnings
❌ Red → Invalid




🛠 Stability & Reliability

Safe defaults prevent crashes due to missing optional values
Validation errors are isolated per row
Invalid rows never contaminate totals or indicators
Clear separation between data quality checking and analysis


⚠️ Known Limitations

Desktop build only (Windows)
Analysis assumes one record per child
Does not currently auto‑repair data (review/export only)


🎯 Intended Users

Nutrition analysts
Monitoring & Evaluation officers
Survey data managers
UNICEF / NGO / Government nutrition programs


✅ Summary
This release delivers a production‑ready IYCF analysis tool with strong emphasis on:

Correct survey logic
Transparent quality control
Robust indicator calculation
Professional reporting outputs

The application is now well‑suited for field data validation, routine survey analysis, and stakeholder reporting.
