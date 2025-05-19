# Harmony Healthcare Emergency Room Analysis Project

## Overview
This project supports Harmony Healthcare in identifying parameters most strongly associated with emergency room visits. The analysis focuses on cleaning and standardizing a complex healthcare dataset and creating visualizations to explore potential correlations between various patient factors and emergency room admissions.

## Dataset
The original dataset consists of 675 columns and 2,822 rows containing patient information, clinical measurements, healthcare utilization metrics, and social determinants of health. The analysis pipeline transforms this raw data into a more manageable and analysis-ready format.

## Key Project Components

### Data Cleaning Pipeline
The project implements a comprehensive data cleaning process:
1. Standardization of inconsistent categorical values
2. Conversion of text to lowercase for consistency
3. Removal of completely blank columns
4. Removal of columns with >80% missing values
5. Engineering of a binary 'Admission' target variable
6. Imputation of missing values (mode for categorical, mean for numerical)
7. Removal of date/temporal variables
8. Final quality checks for remaining missing values

### Target Variable Creation
An 'Admission' binary indicator (Yes/No) is engineered from three ED-related fields:
- ED.Episode.Admit.Location
- ED.HIE.Claim.Location
- ED.HIE.Claim.Discharge

### Data Visualization
The project includes several exploratory visualizations:
- Admission status by education level
- Active medications by admission status
- Racial disparities in admission rates
- HCC risk scores by admission
- Primary care encounter counts
- Social determinants of health assessment counts
- Clinical indicators (BMI, eGFR, fasting glucose)
- Preventive care metrics

## Key Findings

1. **Educational Factors**: Individuals with less than a high school degree show significantly higher ER admission rates.
2. **Medication Management**: Admitted patients have substantially higher numbers of active medications.
3. **Racial Disparities**: Notable differences in admission rates across racial/ethnic groups.
4. **Healthcare Utilization**: Higher primary care utilization correlates with ER admissions, suggesting complex health needs.
5. **Social Determinants**: Patients with more SDOH assessments have higher ER utilization.
6. **Clinical Indicators**: Differences in fasting glucose levels and BMI between admitted and non-admitted patients.

## Feature Selection Results

Using Lasso Regression, the feature selection team identified the following variables as most important predictors of emergency room admissions:

1. Patient.HCC.Risk.Total.Risk
2. Active.Medications
3. Primary.Care.Encounter.Count
4. SDOH.Assessment.Count
5. Patient.Appointment.No.Show.Rate
6. Depression.Screening.Count.Past.Yr
7. eGFR.Result
8. Most.Recent.BMI.Value
9. UDS.Qualifying.Encounter.Count
10. COVID.19.Immunization.Code
11. Fasting.Glucose.Test.Result

These features represent a mix of clinical risk scores, medication burden, healthcare utilization patterns, social determinants of health, appointment adherence, preventive screening, laboratory values, and immunization status - demonstrating the multifaceted nature of factors influencing emergency room utilization.

## Outputs

The project produces several cleaned datasets:
- `NoBlank_data.csv`: Dataset with blank columns removed
- `No_80percent_blanks.csv`: Dataset with high-missing columns removed
- `HHdata_MissingValues_BinaryTarget.csv`: Dataset with binary admission target
- `Categorical.csv`: Dataset with imputed categorical variables
- `Numerical.csv`: Dataset with imputed numerical variables
- `NoDates.csv`: Dataset with date columns removed
- `HHdata_FilledValues_BinaryTarget.csv`: Final cleaned dataset with all preprocessing steps

## Requirements

The R packages required for this analysis:
- readxl
- ggplot2
- dplyr
- scales

## Usage

1. Ensure all required packages are installed using the package management code in the first code chunk.
2. Run each code chunk sequentially to process the data through the cleaning pipeline.
3. Generate visualizations to explore relationships between variables and admission status.

## Implications for Healthcare Planning

The findings suggest several focus areas for Harmony Healthcare:
1. Educational interventions for individuals with lower educational attainment
2. Medication review programs for patients on multiple medications
3. Cultural competence initiatives to address disparities
4. Better coordination between primary care and emergency services
5. Proactive screening for social determinants of health

## Contributors
This project was developed by:
- Bart: Data import, cleaning, visualization
- Daniel: Feature engineering, date removal, text standardization
- Eddie: Dataset production and standardization
