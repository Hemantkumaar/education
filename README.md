# education
The purpose of this project is to see socioeconomic conditions (income, unemployment, family structure, and education levels) relate to high school academic performance measured by ACT/SAT scores. By combining EdGap data with NCES school information, the project aims to highlight patterns and disparities in educational outcomes across schools.

Understanding what drives student performance is one of the most important questions in educational data science. Standardized test outcomes, such as the average ACT score, are commonly used indicators of school performance and college readiness. However, these results are often influenced by broader socioeconomic conditions—including household income, unemployment, and educational attainment levels within communities.

This analysis aims to examine whether school performance, measured by average ACT score, can be predicted by socioeconomic factors. The study primarily uses data from EdGap.org (2016), which provides ACT and socioeconomic characteristics for U.S. school districts, and the Common Core of Data (CCD) from the National Center for Education Statistics, which supplies detailed school-level information. Additionally, a school characteristics dataset is integrated to include more granular predictors such as student–teacher ratio, charter status, and free/reduced lunch participation.

# links
https://www.dropbox.com/scl/fi/fkafjk8902sq8ptxh94r2/ccd_sch_029_1617_w_1a_11212017.csv?rlkey=gucrdz5f6e38bezz2y3yalxbw&e=1&dl=0

# Predicting School Performance from Socioeconomic Factors

## Overview

This project investigates whether school performance, measured by the average ACT score, can be predicted by socioeconomic and school-level factors.  
The analysis integrates multiple datasets to explore how income, education, unemployment, and school characteristics such as student–teacher ratio and charter status relate to academic outcomes.

---

##Data Sources

1. EdGap Data (2016)  
   - Contains average ACT scores and district-level socioeconomic information.  
   - Source: [EdGap.org](https://edgap.org/)

2. Common Core of Data (CCD, 2016–2017)  
   - Provides detailed information on U.S. public schools (enrollment, teachers, charter status, etc.).  
   - Source: [NCES](https://nces.ed.gov/ccd/)

3. School Characteristics Dataset  
   - School-level information including student–teacher ratio, free/reduced lunch, and locale codes.

---

##Steps in Data Analysis

1. **Data Loading**  
   - Imported EdGap, CCD, and School datasets using `pandas`.

2. **Inspection & Cleaning**  
   - Renamed columns to lowercase, snake_case format.  
   - Converted columns to correct data types using `pd.to_numeric()`.  
   - Removed duplicates, missing IDs, and out-of-range values (ACT scores, percentages, etc.).

3. **Merging Datasets**  
   - Joined datasets on the common key `ncessch` (NCES School ID).

4. **Derived Variables**  
   - Created `student_teacher_ratio`, `pct_low_income`, and `log_income`.

5. **Exploratory Data Analysis**  
   - Visualized correlations between ACT and socioeconomic predictors.  
   - Generated scatterplots, boxplots, and correlation heatmaps.

6. **Modeling**  
   - **Baseline model:** Socioeconomic factors only.  
   - **Extended model:** Added student–teacher ratio and charter status.  
   - Compared performance using Adjusted R², AIC/BIC, and cross-validated MAE.

7. **Interpretation & Conclusions**  
   - Found that income, college attainment, and lower lunch participation predict higher ACT scores.  
   - Smaller class sizes (low student–teacher ratios) also improve performance.

---

##Key Files

| File | Description |
|------|--------------|
| `notebooks/Educationfinal.ipynb` | Main analysis notebook with code, figures, and explanations. |
| `data_raw/` | Folder containing raw EdGap, CCD, and school datasets. |
| `data_clean/edgap_extended_clean.csv` | Final cleaned and merged dataset used for modeling. |
| `reports/figures/` | Generated plots (correlation matrix, scatterplots, boxplots). |
| `requirements.txt` | List of Python packages required to run the analysis. |

---

## Results Summary

- Socioeconomic variables explain most variation in ACT scores.  
- Student–teacher ratio and charter status improve predictive accuracy.  
- Smaller class sizes and reduced economic disadvantage correlate with higher ACT performance.  
- Results highlight the importance of both community and school-level resources in shaping educational outcomes.

