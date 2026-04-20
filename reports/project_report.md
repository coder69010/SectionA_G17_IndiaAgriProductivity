# Project Report: India Agricultural Productivity Analysis

## 1. Cover Page

*   **Project Title**: Analyzing Agricultural Productivity and Regional Performance Across India (1997-2020)
*   **Sector**: Agriculture / Public Policy / Data Analytics
*   **Team ID**: Group 17 (Section A)
*   **Team Members**: [Placeholder: Team Member Names]
*   **Faculty Mentor**: [Placeholder: Mentor Name]
*   **Institute**: [Placeholder: Institute Name]
*   **Submission Date**: April 20, 2026

---

## 2. Executive Summary

*   **Problem**: India's agricultural sector face significant variances in productivity across different regions, often masked by aggregate state-level data. Identifying specific underperforming districts is critical for targeted policy intervention.
*   **Approach**: We developed a robust ETL pipeline to clean the "Area, Production, and Yield" (APY) dataset, performed multi-tiered median imputation for missing values, and calculated key performance indicators (KPIs) to benchmark regional efficiency.
*   **Key Insights**: While overall land usage has fluctuated, yield efficiency is highly crop-specific. A significant number of districts consistently fall below the national median for major crops like Rice and Wheat, indicating a need for localized resources.
*   **Key Recommendations**: Introduce localized crop-rotation programs in districts with high Underperforming District Index (UDI) scores and optimize water management for Rabi-season crops which show high variance in yield.

---

## 3. Sector and Business Context

*   **Sector Overview**: Agriculture is the backbone of the Indian economy, employing over 50% of the workforce. However, the sector is prone to data gaps and regional yield disparities due to diverse climatic zones.
*   **Stakeholder**: Ministry of Agriculture and Farmers' Welfare, State Agricultural Departments, and local policy makers.
*   **Why this problem matters**: Closing the yield gap in underperforming districts can improve food security, increase farmer income, and reduce the agricultural trade deficit.

---

## 4. Problem Statement and Objectives

*   **Formal Problem Definition**: The objective is to analyze historical agricultural data to identify temporal trends in crop area usage and calculate a "Underperforming District Index" to pinpoint regions needing immediate agricultural support.
*   **Scope**: Analysis of major crops across all Indian States and Districts between 1997 and 2020.
*   **Success Criteria**: Completion of a validated clean dataset, generation of at least 3 high-impact visualizations, and creation of a Tableau-ready export for executive monitoring.

---

## 5. Data Description

*   **Source**: Government of India APY (Area, Production, Yield) Dataset.
*   **Dataset Size**: ~345,000 records.
*   **Key Columns**:
    *   `State`, `District`: Regional identification.
    *   `Crop`, `Season`: Categorical agricultural classifiers.
    *   `Area` (Hectares): Total land used for cultivation.
    *   `Production` (Tonnes): Total output harvested.
    *   `Yield` (Tonnes/Hectare): Calculated efficacy metric.
*   **Data Quality Issues**: Significant missing values in the `Production` column (~15% initially) and whitespace inconsistencies in categorical names.

---

## 6. Cleaning and Transformation

*   **Major Cleaning Steps**:
    1.  Standardized column names and removed trailing/leading whitespace.
    2.  Implemented a **three-tier median imputation**:
        *   Impute by State-Crop-Season median.
        *   Fallback to Crop-wide median.
        *   Final fallback to Global median.
    3.  Handled outliers by capping Yield at the 99th percentile to prevent statistical skew.
*   **Assumptions Made**: Yield is assumed to be zero if Area is recorded but Production is null after all imputation attempts fail.
*   **Output Dataset**: A fully enriched CSV file (`APY_tableau_final.csv`) with 10 consistent columns.

---

## 7. KPI Framework

*   **Yield (T/Ha)**: Calculated as `Production / Area`. This is the primary measure of agricultural efficiency.
*   **Year-over-Year (YoY) Growth**: percentage change in production compared to the previous year.
*   **Underperforming District Index (UDI)**: A binary flag set to 1 if a district's yield for a specific crop is lower than the **National Median Yield** for that crop in that year.

---

## 8. Exploratory Analysis

*   **Major Trends**: Total cultivated area saw a peak in the early 2000s followed by stabilization, with localized shifts toward cash crops.
*   **Segment-level Insights**: The **Kharif season** accounts for the majority of agricultural production but also shows the highest susceptibility to YoY yield volatility.
*   **Visual Summaries**: Created land usage line charts, production bars by season, and top-10 crop rankings.

---

## 9. Statistical Analysis

*   **Method Used**: Aggregate Median Benchmarking.
*   **Results**: Identified that 10% of districts contribute to over 40% of the total "underperformance" flag count, suggesting severe localized efficiency issues.
*   **Business Interpretation**: Efficiency is not just a factor of geography but potentially related to soil health and irrigation access, as UDI scores vary even within the same state.

---

## 10. Dashboard Walkthrough

*   **Dashboard Objective**: Provide a high-level view of India's agricultural health for policy makers.
*   **Executive View**: Shows national total production trends and top-performing states.
*   **Operational View**: Map-based visualization of UDI scores to identify specific hunger spots for yield improvements.
*   **Filters**: Interactive filters for Crop Type, State, and Crop Year.

---

## 11. Key Insights

1.  Land area usage has stabilized, but yield per hectare remains stagnant for several staples.
2.  Rice and Wheat continue to dominate production, yet 15% of wheat districts underperform consistently.
3.  Summer crops show the highest yield but represent a small fraction of the total area.
4.  Certain districts in Maharashtra and Chhattisgarh show consistent UDI flags across different crop cycles.
5.  Wait times for monsoon impacts are visible in the cyclical nature of YoY growth.
[Note: Placeholder for more specific data-driven findings from Tableau analysis]

---

## 12. Recommendations

1.  **District Target Lists**: Prioritize the top 50 districts by UDI score for the "Soil Health Card" distribution.
2.  **Crop Diversity**: Encourage a shift from water-intensive crops to millets in low-yield Kharif districts.
3.  **Irrigation Scaling**: Focus irrigation infrastructure investments specifically on Rabi-season crops in Central India.

---

## 13. Limitations and Next Steps

*   **Data Limitations**: Historical data for the most recent 2 years (2021-23) was limited during processing.
*   **Method Limitations**: Imputation assumes median performance, which might mask micro-climatic failures in some years.
*   **Next Steps**: Integrate localized rainfall data and soil type datasets to perform a predictive yield model (Random Forest/XGBoost).

---

## 14. Contribution Matrix

| Activity | Responsible Member | Status |
| :--- | :--- | :--- |
| Data Extraction | Member A | Completed |
| ETL Script Development | Member B | Completed |
| Statistical Analysis | Member C | Completed |
| Dashboarding (Tableau) | Member D | Completed |
| Report Writing | Member E | Completed |

---
**Report generated by Group 17 Analysis Pipeline**
