
# 🫁 Lung Cancer Risk Dashboard (Power BI Project)

This Power BI project explores a survey dataset of individuals assessed for lung cancer risks. As a **Data Analyst**, the goal was to extract patterns, trends, and risk correlations that can help in preventive healthcare awareness and decision-making.

---

## 📊 Project Overview

This dashboard summarizes the correlation between smoking, alcohol use, peer pressure, chronic disease, age group, gender, and lung cancer diagnosis.

Using Power BI, we built visualizations to:

- Identify lung cancer prevalence
- Analyze demographic risk factors
- Understand behavioral risk contributors
- Provide actionable health insights

---

## 📁 Dataset Description

- File: `survey lung cancer.csv`
- Rows: 309 respondents
- Target Column:`LUNG_CANCER` (YES/NO)
- Key Features:
  - AGE
  - GENDER
  - SMOKING
  - ALCOHOL CONSUMING
  - CHRONIC DISEASE
  - PEER PRESSURE
  - WHEEZING
  - FATIGUE
  - COUGHING
  - SHORTNESS OF BREATH
  - SWALLOWING DIFFICULTY

---

## ⚙️ DAX Measures & Columns

```DAX
// Total Respondents
Total_Cases = COUNTROWS('survey lung cancer')

// Lung Cancer Cases
Positive_Cases = CALCULATE([Total_Cases], 'survey lung cancer'[LUNG_CANCER] = "YES")

// Lung Cancer Rate %
Lung_Cancer_Rate = DIVIDE([Positive_Cases], [Total_Cases], 0)

// Smoking Risk Index (custom metric)
Smoking_Risk_Index = 
CALCULATE(DISTINCTCOUNT('survey lung cancer'[SMOKING]), 'survey lung cancer'[LUNG_CANCER] = "YES")

// Age Groups
Age_Group = 
SWITCH(
    TRUE(),
    'survey lung cancer'[AGE] <= 30, "18–30",
    'survey lung cancer'[AGE] <= 50, "31–50",
    'survey lung cancer'[AGE] <= 70, "51–70",
    "70–87"
)

📌 Observations Board
High Cancer Rate: 87% of respondents were diagnosed with lung cancer.

Age 51–70 Group Dominates: This age bracket had the highest cancer incidence.

Smoking Strongly Correlates: Most lung cancer patients are smokers.

Peer Pressure: Balanced risk between those who felt pressure and those who didn’t.

Chronic Diseases: Slightly higher cancer risk among people with chronic illness.

Alcohol Impact: Higher lung cancer diagnosis was observed among alcohol consumers.

Gender Split: More female cancer patients than male, despite more male respondents.

Fatigue and Wheezing: Strong visual correlation with positive diagnoses.

Swallowing Difficulty: Majority of patients with swallowing difficulty had cancer.

18–30 Age Group Least Affected: Very low diagnosis rate among the youngest group.

✅ Recommendations Board
Target Smoking Cessation Programs for adults aged 51+.

Public Awareness Campaigns linking smoking, drinking, and lung health.

Early Screening for individuals with chronic diseases.

Specialized Healthcare Resources for females over 50.

Behavioral Health Support to manage peer pressure among youth.

Fatigue and Wheezing should be early diagnostic flags.

Age-Specific Campaigns targeting high-risk age brackets.
