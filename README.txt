Assignment 1: Data Profiling (EDA) Report - Book Retail
This repository contains the Jupyter Notebook for Assignment 1, which focuses on Data Profiling and Exploratory Data Analysis (EDA). The project uses real-world book sales and review data to diagnose and handle common data quality issues such as missing values, outliers, inconsistencies, and PII/bias risks.

Group Members
Name	Matric Number
NURUL AMNIE BINTI SALEHUDDIN		A210070
AINESH AVIGNA A/L GUNASEELEN		A214184
FARISYA AFIFI BINTI MUHAMMAD NUH	A209899
NURUL SYAFIYAH HANI BINTI BAHARUDIN	A210643

Scenario:  
-large-scale online book retailer such as Amazon Books receives thousands of customer reviews daily. Before this raw review data can feed into a sentiment-analysis pipeline, it must be profiled and cleaned of missing values, price outliers, inconsistent formats, and PII risks.

-He, Hollenbeck, and Proserpio (2022) documented that the market for fake reviews on Amazon is significant — meaning raw e-commerce review data is inherently noisy and requires rigorous cleaning before analysis. Positivity bias in online reviews is also well established in the literature (e.g., Hu, Pavlou & Zhang, 2009), which makes rating-skew profiling an essential preprocessing step.


Business Question: How can we automate the profiling and cleaning of raw customer review data to identify data quality issues (such as missing values, price outliers, and PII risks) before the data can be used for customer sentiment analysis?

Justification (Based on the INFORMS Article):

This scenario is grounded in real-world industry challenges. A study by He, Hollenbeck, and Proserpio (2022) in Marketing Science revealed that the market for fake reviews on Amazon is significant. The research found that firms purchase fake reviews to manipulate ratings, which directly impacts data quality. The study showed that after firms stop buying fake reviews, their average ratings fall and the share of one-star reviews increases significantly, particularly for young products. This proves that raw review data from e-commerce platforms like Amazon inherently contains serious data quality issues, including rating bias and manipulation. Therefore, the process of profiling and cleaning data is a critical, real-world necessity before any sentiment analysis can be performed.

Reference:

He, S., Hollenbeck, B., & Proserpio, D. (2022). The Market for Fake Reviews. Marketing Science, 41(5), 896-921. https://doi.org/10.1287/mksc.2022.1353

Data Source
The data for this project is provided as two CSV files:

Top-100_Trending Books.csv

customer_reviews.csv

Both files must be placed in the same directory as the notebook.

Data Profiling and Issue Handling
1. Missing Values
Books Dataset: 3 missing values found in the rating column.

Handling: Flagged with a new column rating_missing. Missing values were imputed with the median rating to retain rows for analysis.

Reviews Dataset: No missing values found.

2. Outliers
Books Dataset: Boxplot revealed a potential outlier (book price = $48.77).

Handling: Outliers capped at the 99th percentile in a new column book price_capped. Original data preserved.

3. Other Quality Issues
Inconsistent Format: Leading space in author name (' Wendy Loggia') was fixed using .str.strip().

Inaccurate Data: Wrong author for "Balloons over Broadway" (Rank 31) was corrected to "Melissa Sweet".

Wrong Data Type: The date column was a string and was converted to a datetime object.

Duplicates: None found in both datasets.

4. PII and Bias Risks
PII Risk: The reviewer column contains names, which were anonymized using SHA-256 hashing (reviewer_hashed). The original column was dropped.

Bias Risk: The rating distribution is heavily skewed towards positive reviews (4 and 5). This positivity bias, consistent with the fake review findings of He et al. (2022), must be noted as a limitation.

Exploratory (Diagnostic) Charts
The notebook includes:

Missing Value Heatmap - visualizes missing rating values.

Boxplots (Before and After) - shows the effect of outlier capping.

Bar Chart: Ratings Distribution - highlights positivity bias.

Bar Chart: Top Authors (After Cleaning) - shows corrected author counts.

Conclusion
After a thorough profiling and cleaning process, both datasets are fit for basic descriptive analysis and visualization. We successfully handled missing values, corrected inaccuracies, and mitigated PII risks.

Limitations remaining:

Sample Bias: The "Top 100" list is a snapshot, not a representative sample.

Review Bias: Overwhelmingly positive reviews limit sentiment analysis, and may reflect the rating manipulation documented by He et al. (2022).

Imputation: The 3 imputed ratings are estimates.

Instructions to Run the Notebook
Prerequisites: Install the required libraries:

bash
pip install pandas numpy matplotlib seaborn
Clone the Repository:

bash
git clone https://github.com/a209899-Fify/assignment1-Data-Profiling-EDA-.git
cd assignment1-Data-Profiling-EDA-
Ensure Data Files are Present in the same directory as the notebook:

Top-100_Trending Books.csv

customer_reviews.csv

Run the Notebook: Open the .ipynb file in Jupyter Lab, Jupyter Notebook, or Google Colab and run all cells from top to bottom. The notebook is fully executable and self-contained.
