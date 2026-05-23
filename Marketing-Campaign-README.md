# 📣 Marketing Campaign Analysis — Power BI Dashboard

An end-to-end **Marketing Analytics** project built in **Power BI**, transforming raw customer and campaign data into an interactive dashboard that helps marketing teams understand their customer base, evaluate campaign performance, and identify the most valuable segments to target in future campaigns.

---

## 🎯 Project Overview

Marketing budgets are finite — the question is always *which customers should we target, and which campaigns actually work?* This project analyzes a marketing dataset of **2,240 customers** to:

- Profile the **customer base** across demographics (age, income, education, family)
- Measure **campaign performance** and identify which segments respond best
- Apply **RFM segmentation** (Recency, Frequency, Monetary) to classify customers by value
- Surface **purchasing patterns** across products and channels
- Recommend **targeted marketing strategies** for the highest-value segments

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Data modeling, visualization, and reporting
- **Power Query (M)** — Data cleansing, transformation, and feature engineering
- **DAX** — Custom measures and KPIs
- **One Big Table (OBT) modeling** — Chosen over star schema given the small, single-source dataset
- **RFM Segmentation Model** — Marketing-standard customer value framework

---

## 🧹 Data Preparation Highlights

The raw dataset required substantial cleaning and enrichment before analysis:

### Cleaning
- Stripped leading/trailing whitespace from column names
- Cleaned the `Response` column (non-numeric characters) and converted to binary (0/1)
- Imputed missing `Income` values using the **median** (chosen because the distribution is right-skewed)
- Removed unrealistic `Year_Birth` outliers (rows with birth year < 1920)
- Capped `Income` outliers at the **99th percentile** to reduce skewness while retaining most data
- Standardized `Marital_Status` categories — grouped invalid values like "Alone", "Absurd", "YOLO" into `Single`
- Corrected data types across all 29 columns

### Enrichment (Engineered Features)
| Feature | Description |
|---------|-------------|
| `Age` | Calculated from `Year_Birth` |
| `Customer_Generation` | Generational cohort (Baby Boomer, Gen X, etc.) |
| `Dependents` | Sum of `Kidhome` + `Teenhome` |
| `Has_children` | Binary indicator |
| `IncomeLevel` / `Income (bins)` | Categorical income brackets |
| `Total_spent` | Sum across all product spend columns |
| `Total Purchase` | Sum across deals/web/catalog/store purchases |
| `Total_campaigns` | Sum of accepted campaigns 1–5 |
| `ResponseToAnyCampaign` | Binary — accepted any campaign? |
| `R_Score`, `F_Score`, `M_Score`, `RFM` | RFM model components & combined score |
| `Segment` | Customer segment derived from RFM |
| `AgeGroup`, `TotalFoodExpenditure` | Additional analytical groupings |

---

## 📑 Report Pages

The Power BI dashboard is organized into **three focused pages**, each serving a distinct business question:

### 1. 👥 Customers Page
A comprehensive overview of who the customers are — their demographics, behavior, and key characteristics.

**KPIs:** No. of Customers • Avg Age • Avg Income • Avg Dependents • Avg Tenure

**Key visuals:** Customer distribution by Income, Age, Marital Status, Education, and Dependents, plus a dynamic Median Income by Demographics chart with a field parameter for slicing.

### 2. 📊 Campaigns Page
Evaluates response rates across all 6 marketing campaigns and identifies which customer segments engage most.

**KPIs:** Campaign 1–5 Response Rates • Last Campaign Response Rate • Overall Response Rate

**Key visuals:** Response Rate vs. Dependents, Campaigns vs. Age, and Campaigns vs. Demographics.

### 3. 💰 Purchasing & RFM Segmentation Page
Categorizes customers by purchasing patterns using the RFM framework and identifies high-value segments to focus on.

**Key visuals:** High-Value Customer matrix (Loyal vs. Potential Loyal), Food vs. Wine purchasing across age, RFM classification table, and a dynamic Purchasing Patterns by Demographics chart.

---

## 🔍 Key Insights & Findings

### Customer Profile
- **Majority middle-income:** The largest customer group sits in the ~$50K income bracket (1,600+ customers combined)
- **Core age range:** Customers in their **40s–60s** dominate the base (50s alone = 676 customers)
- **Highly educated base:** 1,127 customers hold a Graduation degree, plus 485 PhDs and 370 Masters
- **Family-oriented:** Customers with **one dependent** form the largest group (1,125 customers)

### Campaign Effectiveness — The Winning Profile
The customers most likely to accept campaigns share a clear profile:
- **Single** customers
- **PhD holders**
- **High income** earners
- Customers with **no kids**

These four traits consistently appear in the highest-response segments across nearly every campaign.

### RFM Segmentation
- **Potential Loyal Customers** make up **~34% of the customer base** — the single biggest opportunity for targeted marketing investment
- This segment tends to have **more dependents**, prefers **deals/discounts**, and favors **in-store purchases**
- Strong upside opportunity to grow **wine and meat** sales within this group

### Purchasing Behavior by Age
- **Young customers (20s–30s):** Prefer **food** over wine
- **Older customers (60+):** Strongly skew toward **wine** purchases
- These behavioral differences should drive distinct campaign creative and product positioning by age cohort

### 🔥 Standout Insight
> **Customers with no kids spent 7x more than customers with kids.**
> This is the single most actionable finding in the dataset and should heavily influence segmentation strategy.

---

## 💡 Business Recommendations

1. **Prioritize the Potential Loyal segment (~34% of base)** — This is the largest untapped opportunity. Build campaigns specifically designed around their preferences: discount-driven offers, in-store experiences, and family-friendly bundles.

2. **Target the high-response profile aggressively** — Single, highly educated, high-income, childless customers respond best. Future campaigns should over-index on reaching this profile.

3. **Differentiate creative by age cohort:**
   - **20s–30s:** Affordable, trendy, health-focused food products
   - **40s–50s:** Premium wines with loyalty discounts
   - **60+:** Wine-focused premium experiences

4. **Audit underperforming campaigns** — With overall response rates varying widely across the six campaigns, lower-performing ones should be redesigned or retired.

5. **Build a "no kids" premium tier** — Given the 7x spend difference, this segment deserves its own dedicated marketing track focused on personal-luxury categories like wine and gold products.

---

## 📁 Repository Contents

```
📦 Marketing-Campaign-Analysis-PowerBI
 ┣ 📄 Marketing_Camp.pbix              # Power BI report file
 ┣ 📄 Data_Preparation.docx            # Data cleaning & feature engineering documentation
 ┣ 📄 Dashboard_Explaination.docx      # Page-by-page dashboard walkthrough & insights
 ┗ 📄 README.md
```

---

## 🚀 How to Use

1. Clone or download this repository.
2. Open `Marketing_Camp.pbix` in **Power BI Desktop** (latest version recommended).
3. Navigate the three report pages — **Customers**, **Campaigns**, and **Purchasing & RFM** — to explore the data interactively.
4. Refer to the included `.docx` files for full documentation of the data preparation methodology and the business rationale behind every visual.

---

## 📈 Skills Demonstrated

- **End-to-end BI workflow** — from raw data ingestion through executive-ready dashboard
- **Power Query (M)** — data cleansing, outlier handling, missing value imputation, data type management
- **Feature engineering** — built 17+ analytical features including RFM scoring
- **DAX measure development** — KPIs, response rates, segmentation logic
- **Customer segmentation** — applied the industry-standard RFM model
- **Marketing analytics** — translated raw data into campaign strategy and audience targeting
- **Business storytelling** — turned visuals into clear recommendations stakeholders can act on

---

## 📬 Contact

If you have questions, feedback, or want to connect:

- **GitHub:** [your-github-username](https://github.com/kariman29)
- **LinkedIn:** [linkedin-profile](https://www.linkedin.com/in/karimanibrahem45/)
---

⭐ *If you found this project helpful or inspiring, please consider giving it a star!*
