# Life Expectancy — Preprocessing & EDA

## Project Overview
This notebook preprocesses and explores a Life Expectancy dataset to prepare it for analysis or modeling. The main goals are:

- Clean and standardize the raw data  
- Handle missing values and outliers thoughtfully  
- Produce concise exploratory visualizations  
- Save a cleaned dataset and example figures for reporting  

---
## Tools & Libraries

This project was developed using the following tools:

- **Python 3.x** — core programming language  
- **Pandas** — data manipulation and preprocessing  
- **NumPy** — numerical computations and array handling  
- **Matplotlib** — base plotting library  
- **Seaborn** — statistical data visualization  
- **Scikit-learn** — machine learning utilities (e.g., `KNNImputer`)  
- **Jupyter Notebook** — interactive environment for development and analysis  


---

## Dataset
**File referenced in notebook:** `Life Expectancy Data.csv`  
*(original path: `C:\\Users\\HP\\Downloads\\Life Expectancy Data.csv`)*

Typical columns include demographic and health indicators (e.g., `BMI`, `Infant deaths`, `Adult Mortality`, `GDP`, `Life expectancy`, etc.).  
The notebook assumes these columns and performs column-name cleaning as a first step.

---

## Notebook Summary — Key Steps
1. **Import necessary libraries**  
   - `pandas`, `numpy`, `matplotlib/pyplot`, `seaborn`, `scikit-learn`.  

2. **Read datasets**  
   - Loads `Life Expectancy Data.csv` with `pd.read_csv(...)`.  
   - Strips and normalizes column names (removes leading/trailing spaces).  

3. **Sanity checks**  
   - `df.head()`, `df.info()`, `df.describe()` and checks for nulls and data types.  

4. **Exploratory Data Analysis (EDA)**  
   - Univariate plots (boxplots, histograms) for numeric columns.  
   - Scatterplots and correlation heatmaps to inspect relationships with `Life expectancy`.  

5. **Missing Value Treatment**  
   - Uses `KNNImputer` (and/or other imputation strategies) to fill missing numeric values.  
   - Demonstrates both column-wise and full-matrix imputation; recommended approach: impute numeric columns together to preserve relationships.  

6. **Outlier Treatment**  
   - Tukey IQR (lower/upper whisker) approach used to compute bounds and cap outliers.  
   - Example:
     ```python
     data[col] = np.where(data[col] < lw, lw, data[col])
     data[col] = np.where(data[col] > uw, uw, data[col])
     ```  

7. **Duplicates and garbage values**  
   - Removes duplicates and replaces or flags obviously invalid values.  

8. **Save cleaned dataset and visualizations**  
   - Saves figures (e.g., `images/boxplots_grid.pdf`, `images/highest_salary.png`)  
   - Saves cleaned dataframe (`output/life_expectancy_cleaned.csv`).  

---
## Key Findings 

Life expectancy correlates strongly with GDP, BMI, and Adult Mortality.

Missing-value patterns were non-random (certain health metrics missing by country/year).

After capping outliers and imputing, distributions are more stable and suitable for modeling.

Next Steps

Train regression or tree-based models to predict Life expectancy.

Build an interactive dashboard (Streamlit or Plotly Dash).

Automate the preprocessing pipeline with scikit-learn Pipeline.

Add tests and modularize reusable preprocessing functions.
## How to Run (Reproduce)
1. Clone the repo and place the dataset in the `data/` folder or update the path in the notebook.  



#Author

##RAHMA SABER — Data Preprocessing & EDA

