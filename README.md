# ⚖️ Nutrition Paradox: Global Health & Nutrition Analytics

## Project Statement
> This project investigates the "Nutritional Paradox"—the simultaneous rise of obesity and the persistence of malnutrition—using publicly available data from the World Health Organization (WHO). By integrating Python for ETL, SQL for structured storage, and Power BI/Streamlit for visualization, this analysis aims to inform global health strategies.

## 🚀 Project Overview
The "Nutrition Paradox" refers to the complex challenge where undernutrition and overnutrition coexist within the same regions or even households. This project analyzes trends across countries, age groups, and genders between 2012 and 2022.

## 🛠 Technical Stack
* Language: Python
* Libraries: Pandas, Seaborn, Matplotlib, Plotly, Pycountry
* Database: SQL (MySQL / PostgreSQL / SQLite)
* Visualization: Power BI or Streamlit

## 📂 Dataset Details
Data is sourced via the WHO API for four key indicators:
* **Obesity (Adults)**: BMI ≥ 30 (Dataset: NCD_BMI_30C).
* **Obesity (Children)**: BMI +2SD from median (Dataset: NCD_BMI_PLUS2C).
* **Underweight (Adults)**: BMI < 18.5 (Dataset: NCD_BMI_18C).
* **Thinness (Children)**: BMI -2SD from median (Dataset: NCD_BMI_MINUS2C).

## ⚙️ Project WorkflowStep 
1. Data Collection & Preprocessing
    * Load 4 datasets from WHO API endpoints.
	* Assign age_group ("Adult" vs "Child/Adolescent").
    * Combine into two master DataFrames: df_obesity and df_malnutrition.
    * Filter for the timeframe: 2012 – 2022.
2. Cleaning & Feature Engineering
	* **Standardization**: Mapping TimeDim to Year, Dim1 to Gender, and NumericValue to Mean_Estimate.
    * **Geography**: Use pycountry to convert ISO Alpha-3 codes into full country names.
    * **Feature Creation**:
    	* **CI_Width**: Calculated as $UpperBound - LowerBound$.
    	* **Obesity Level**: Categorized as High ($\ge 30$), Moderate ($25–29.9$), or Low ($< 25$).
    	* **Malnutrition Level**: Categorized as High ($\ge 20$), Moderate ($10–19.9$), or Low ($< 10$).
3. Exploratory Data Analysis (EDA)Using Matplotlib and Seaborn to identify:
    * Data shape, structure, and missing values.
    * Distribution of Mean_Estimate and CI_Width.
    * Regional trends and gender-based disparities.
4. SQL Implementation:
    * Establish connection (e.g., mysql.connector or sqlite3).
    * Create tables: obesity and malnutrition.
    * Data Insertion: Migrating cleaned DataFrames into SQL tables using .iterrows() with batch commits to ensure performance.
	
## 🔍 Key Analytical Queries
project includes 25 SQL queries focused on:
  * Obesity: Top 5 regions by prevalence, trends in India, and gender-based averages.
  * Malnutrition: African region trends, year-over-year changes in Nigeria/Brazil, and countries with increasing malnutrition.
  * Combined Analysis: Side-by-side regional comparisons and identifying countries where obesity is rising while malnutrition is falling.

## 📊 Visualizations & Insights
**Power BI Dashboard / Streamlit App**
	Global Trends: Line charts showing the trajectory of health indicators.
	Risk Maps: Interactive choropleth maps highlighting high-risk nations.
	Demographic Drills: Decomposition trees focusing on Region $\rightarrow$ Country $\rightarrow$ Age Group.
	
## 🎯 Domain & Business Use Cases
**Domain:** Global Health & Nutrition Analytics

**📊 Business Use Cases**
    * Nutrition Risk Monitoring: Identify countries requiring urgent public health intervention.
    * Demographic Analysis: Understand how gender and age groups contribute differently to statistics.
    * Policy Planning: Prioritize regions for funding based on multi-dimensional data.
    * Public Health Reporting: Summarized dashboards for NGOs and governments.

## 🏁 Expected Results
  * Two clean, structured SQL tables (obesity and malnutrition).
  * A Python notebook containing EDA and the results of 25 SQL queries.
  * Comprehensive Power BI Dashboards or a Streamlit UI featuring 10–20+ visualizations.
  * Summary analysis highlighting the coexistence of obesity and malnutrition globally.

## 💡 Summary of Findings
  * Urgent Intervention: Identifying regions with "Double Burden" where both indicators are high.
  * Data Reliability: Using CI_Width to flag regions where data reporting is inconsistent or lacks precision.
  * Vulnerability: Pinpointing specific age groups or genders most affected by the nutrition paradox.

## ⚖️ The Nutritional Paradox: Summary Analysis
The "Nutrition Paradox" refers to the complex global health scenario where high rates of overnutrition (obesity) and undernutrition (malnutrition) exist within the same regions, countries, and sometimes the same households. This project utilized WHO data from 2012 to 2022 to map these disparities across adults and children.

## 📌 Key Insights
  * **Africa & South-East Asia** face persistent malnutrition challenges
  * High-income regions show consistently rising obesity
  * **Female obesity** exceeds male in many countries
  * **Children** show **dual burden** (malnutrition + rising obesity)
  * High CI Width regions indicate unreliable reporting


