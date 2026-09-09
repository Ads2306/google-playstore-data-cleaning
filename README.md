#  Google Play Store — Data Cleaning, Unit Standardization & Exploratory Analysis

- An end-to-end exploratory data analysis (EDA) and data wrangling project on the Google Play Store dataset ($N \approx 10,800$ raw app records). This project focuses on cleaning messy real-world strings, standardizing multi-unit values (bytes, currency, installs), removing deduplicated reviews, and uncovering store-wide app metrics.

###  Executive Summary

- This study processes raw mobile application metrics from the Google Play Store to resolve inconsistent data formatting, missing values, and duplicate listings, enabling precise query-based insights into app distribution, pricing outliers, and popularity metrics across categories.

### Key Insights

- Dominant Category: Family ($1,874$ apps) and Game ($945$ apps) are the largest categories by volume.
- Review Champion: Facebook leads all applications on the platform with over 78.1 million reviews.
- Pricing Anomalies: The most expensive applications belong to the Lifestyle and Finance categories, with luxury/niche apps priced up to $400.00.
- Top Paid Game: "The World Ends With You" stands as the highest-priced game on the platform at $17.99.
- Fintech Leader: Google Pay ranks as the most popular Finance app, passing 100M+ installs.

###  Data Stack & Tools

- Language: Python 3.x
- Data Wrangling: pandas, numpy
- Visualization & Profiling: seaborn, missingno

###  Data Cleaning & Pipeline Transformations

A major portion of this project focuses on string parsing and numerical standardization:

1. Rating Imputation & Outlier Removal:
  - Capped erroneous ratings $>5.0$ to NaN and imputed missing values using the mean rating ($\approx 4.19$).

2. Deduplication via Smart Grouping:
  - Identified 1,979 duplicate app listings.
  - Sorted records by App title and Reviews count, dropping earlier duplicates while retaining only the latest entry with the highest review count.

3. Size Unit Conversion (To Bytes):
  - Parsed string suffix indicators (M for Megabytes, k for Kilobytes).
  - Converted values to exact byte counts ($1\text{ MB} = 1024 \times 1024\text{ bytes}$) and handled "Varies with device" values cleanly.

4. Monetization & Install Cleaning:
  - Stripped special characters (+, ,, $) from Installs and Price fields to cast them into numeric types (float64 / int64).
  - Engineered an auxiliary categorical column Distribution (Free vs Paid).

###  Key Business & Portfolio Takeaways

1. Freemium Dominance: Over $90\%$ of store listings use the Free distribution model, deriving revenue from ads or in-app purchases rather than upfront fees.
2. Category Saturation: Developing in Family or Tools requires strong SEO strategy due to market saturation ($>2,700$ combined listings).
3. Data Quality Matters: Real-world app store data contains heavy noise (e.g., character-encoded numbers, mixed measurement units). Establishing an automated ETL cleaning pipeline is essential prior to modeling.
