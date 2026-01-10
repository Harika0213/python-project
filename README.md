Financial Transaction Data: Cleaning & Analytical Pipeline A Python-based data engineering and analytics project designed to transform uncleaned, multi-currency financial records into a structured format for behavioral spending analysis.

📌 Project Overview Financial data is often messy, containing inconsistent date formats, mixed currencies, and missing categories. This project provides a robust automated pipeline to:

Standardize erratic transaction records.

Enrich data with time-series features and spending tiers.

Visualize key financial metrics like category-wise spending and liquidity impact.

🛠️ Tech Stack Language: Python 3.x

Libraries: Pandas, NumPy, Matplotlib, Seaborn, Regular Expressions (re)

Environment: Jupyter Notebook

📂 Dataset Breakdown Uncleaned_Finance_Data.csv: The raw input featuring inconsistent date formats (dots, slashes, dashes), placeholder values ("???"), mixed currency symbols ($, INR, EUR), and typos in account types.

Cleaned_Financial_Data_Analysis.csv: The final output after the pipeline, featuring 21 standardized columns ready for BI tools or further modeling.

⚙️ Data Cleaning & Engineering Steps The pipeline executes the following logic (as seen in Financial_Data_Cleaning_Analysis.ipynb):

Junk Filtering: Removed records with missing Transaction IDs and placeholder categories.

Date Standardization: Converted multiple date strings into a unified datetime64 format.

Intelligent Category Filling: Used Regex-based keyword matching on transaction descriptions to fill missing categories (e.g., matching "Uber" to "Travel").

Currency Normalization: Extracted currency symbols and converted all amounts into a unified Amount_USD column using static conversion rates.

Sign Correction: Implemented logic to ensure "Expenses" (e.g., Dining, Rent) are consistently negative and "Income" (e.g., Salary, Refund) are positive.

Feature Engineering: * Created Year, Month, and Day_of_Week for seasonal analysis.

Developed a Spending_Tier (Low, Medium, High) based on transaction magnitude.

Calculated Spending_Ratio_Pct to determine the impact of a transaction relative to the available balance.

📊 Key Insights Liquidity Impact: Calculated the "Original Money" (balance prior to transaction) to see which expenses drained the highest percentage of the user's account.

Category Pareto: Identified top spending categories and standardized merchant names (e.g., fixing "Co" to "Electric Co").

Standardization Success: Reduced account types from various typos down to 6 core standardized categories.

