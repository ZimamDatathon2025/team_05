# Blood Transfusion Timing Analysis - MIMIC-IV v3.1 Validation

## Overview
This repository contains validation analyses for blood transfusion timing strategies using **MIMIC-IV v3.1** database. The study examines outcomes for early versus late transfusion strategies in ICU patients, with special focus on cardiovascular cohorts.

## Research Question
**Does the timing of blood transfusion (based on hemoglobin thresholds) affect patient outcomes in critically ill patients?**

## Key Analyses

### 1. **Transfusion Group Classification**
- **Early transfusion**: Hemoglobin (Hgb) ≥ 8 g/dL
- **Late transfusion**: Hemoglobin (Hgb) < 8 g/dL

### 2. **General Population Analysis**
- Base cohort characteristics (demographics, hemoglobin levels)
- Summary statistics by transfusion group
- Gender, age, race, and ethnicity distributions
- Hemoglobin band distributions (stratified by severity)
- Mortality rates and ICU length of stay

### 3. **Cardiovascular Cohort Analysis**
Focused analysis on patients with primary cardiovascular diagnoses, including:
- Pre- and post-transfusion hemoglobin changes (Δ Hgb)
- Timing to first transfusion after ICU admission
- Hospital mortality rates
- Admission type (elective vs. emergency)
- Demographics (gender, age groups, race, insurance, admission type)

### 4. **Top Primary Diagnoses**
Identification of the top 5 primary diagnoses among transfusion patients in each group.

## Data Source
**MIMIC-IV v3.1** (Medical Information Mart for Intensive Care)
- `physionet-data.mimiciv_3_1_icu.*` - ICU events and stays
- `physionet-data.mimiciv_3_1_hosp.*` - Hospital admissions, lab events, patients, diagnoses

### Key Variables
- **RBC Transfusion Item IDs**: 225168, 226368, 227070, 221013
- **Hemoglobin Lab Item IDs**: 50811, 51222, 51640
- **Pre-transfusion window**: 24 hours before transfusion
- **Post-transfusion window**: 6-48 hours after transfusion

## Methodology

### Cohort Selection
1. Identified all ICU patients receiving RBC transfusions
2. Retrieved pre-transfusion hemoglobin values (within 24h)
3. Classified patients into Early/Late transfusion groups
4. Linked demographics, outcomes, and diagnoses

### Statistical Summaries
- Patient counts and percentages
- Mean, median, min, max, standard deviation for continuous variables
- Mortality rates
- Length of stay in ICU

### Cardiovascular Subgroup
Filtered to primary cardiovascular diagnoses using ICD codes containing:
- Cardiovascular, coronary, heart, valve, myocardial conditions

## Key Findings
The analysis generates comprehensive demographic and outcome comparisons between early and late transfusion groups, enabling:
- Assessment of transfusion timing strategies
- Identification of outcome differences
- Understanding of patient characteristics in each group

## Outputs
All results are exported as CSV files:
- `summary_results.csv`
- `gender_distribution.csv`
- `age_distribution.csv`
- `race_distribution.csv`
- `hgb_band_distribution.csv`
- `demographics_full.csv` (cardiovascular cohort)
- Subgroup CSVs by age, gender, race, insurance, admission type

## Visualizations
- Age group distribution by transfusion timing
- Hospital mortality comparison (cardiovascular patients)

## Technical Notes
- Analysis performed using **Google BigQuery** via Python client
- Google Colab environment
- Data tables loaded with `google.colab.data_table` extension
- Matplotlib and Seaborn for visualizations

## Dependencies
```
google-cloud-bigquery
pandas
matplotlib
seaborn
```

## Usage
This notebook validates transfusion strategy outcomes using MIMIC-IV v3.1, providing robust evidence for clinical decision-making regarding optimal transfusion thresholds in ICU settings.

---
**Dataset**: MIMIC-IV v3.1  
**Platform**: Google Cloud BigQuery  
**Environment**: Google Colab
