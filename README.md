# **E‑Commerce Data Cleaning & Analytics Pipeline (BigQuery + Power BI)**

This project delivers a complete data‑engineering and analytics workflow for a multi‑sheet e‑commerce dataset. It includes a **modular BigQuery cleaning pipeline**, a **validated cleaned dataset**, and a **Power BI dashboard** that uncovers key commercial, operational, and customer insights. The repository demonstrates real‑world data issues, robust SQL cleaning logic, and business‑ready analytics.

---

## **Project Overview**

The dataset originates from three raw CSV sheets containing realistic e‑commerce inconsistencies: invalid emails, mixed date formats, inconsistent categories, negative values, and duplicate customer records. The goal of the project is twofold:

1. **Build a reproducible BigQuery pipeline** that merges, standardizes, and cleans the raw data into a single analysis‑ready table.
2. **Perform a full exploratory and KPI‑driven analysis** using Power BI to evaluate sales performance, order outcomes, customer quality, and channel efficiency.

The final output is a **cleaned_orders.csv** file and a **Power BI dashboard** that provides actionable business insights.

---

## **Data Cleaning Pipeline (BigQuery)**

The cleaning workflow is implemented as a sequence of modular SQL scripts:

- Combine raw sheets into a unified staging table.  
- Standardize column names using consistent snake_case formatting.  
- Fix data types for dates, prices, quantities, booleans, and ages.  
- Clean and validate emails, removing invalid characters and flagging incorrect formats.  
- Normalize country values (e.g., GB, U.K., United Kingdom → UK).  
- Standardize categorical fields such as order status, product category, and marketing channel.  
- Remove duplicates using business‑logic keys and eliminate null or invalid rows.  
- Export the final cleaned dataset for BI and modeling.

The result is a **fully standardized, deduplicated, and validated dataset** ready for downstream analytics.

---

<img width="1125" height="633" alt="Sales DB" src="https://github.com/user-attachments/assets/b733f233-b396-47af-92ad-d389a00027fb" />



---



<img width="893" height="484" alt="Quality DB" src="https://github.com/user-attachments/assets/3d02f8e7-df9b-4773-b65c-9915269ac439" />


---
## **Exploratory Analysis (Initial Checks)**

Before building KPIs, several validation checks were performed:

- Order dates show continuous activity with no missing clusters.  
- Instagram and Email appear as the most frequent acquisition channels.  
- Footwear and Accessories dominate the product mix.  
- Order statuses include a realistic distribution of Completed, Pending, Cancelled, and Refunded.  
- Customer behavior includes both first‑time and returning buyers.

These checks confirm that the cleaned dataset is stable and suitable for deeper analysis.

---

# **Business Insights (Power BI Analysis)**

Using the cleaned dataset, a full KPI and operational analysis was performed. The findings below summarize the commercial, operational, and customer‑quality performance of the business.

---

## **Sales Performance**

- **Total Sales:** £62,000  
- **Total Orders:** 1,000  
- **Average Order Value (AOV):** £43  

Monthly revenue shows a stable baseline followed by dramatic spikes:

- **Jan–Apr:** ~£3,500 average per month  
- **April:** £18,600  
- **May:** £27,000  

These surges indicate successful campaigns or product pushes, but also highlight volatility.

### **Sales by Category**
- **Clothing:** £28,000  
- **Accessories:** £21,000  
- **Footwear:** £13,000  

### **Sales by Channel**
- **Instagram:** £27,600  
- **Email:** £17,000  
- **TikTok:** £9,300  
- **Facebook:** £7,500  

Instagram is the strongest revenue driver, while Facebook underperforms and contributes disproportionately to refunds.

---

## **Order Outcomes & Operational Health**

Order completion is low, revealing operational bottlenecks:

- **Completed:** 35%  
- **Cancelled:** 19.5%  
- **Refunded:** 20.6%  
- **Pending:** Remaining balance (significant backlog)

### **Refund Rate by Channel**
- **Facebook:** 56% (critical issue)  
- **Instagram:** 24%  
- **Email & TikTok:** Moderate and stable  

### **Cancellation Rate by Payment Type**
- Highest 26,3%: **PayPal**  
- Following with small difference: **Card**, **Apple Pay**  
- Lowest: **Google Pay** (<10%)  

Units sold follow the same pattern as revenue, with a dramatic increase in May and June.

---

## **Customer & Data Quality Insights**

The customer base appears relatively young, with an **average age of 26**. However, age-related insights should be interpreted cautiously because only 50% of customers provided their age.
Customer data quality is a major concern:

- **Email Validity:** 35% (critical issue) 
- **Newsletter Signup:** 38%  

Using a weighted scoring model (70% email validity, 30% newsletter signup):

- **Data Quality Score:** **36%**

This severely limits CRM, remarketing, and lifecycle automation potential.

---

A GitHub‑ready version using **bold titles** looks like this, keeping the tone concise and analytical while matching the formatting style you’re using across the README:

## **Business Impact**

The dataset covers a short operational period, which limits the ability to make confident long‑term predictions or assess seasonality. Observed patterns may not fully represent typical business performance.

The combined analysis highlights several strategic risks and opportunities:

- **Data volatility** makes it difficult to establish stable performance baselines.  
- **Revenue is campaign‑dependent**, with large spikes masking underlying instability.  
- **Operational inefficiencies** (refunds, cancellations, pending orders) are eroding margin and customer trust.  
- **Facebook acquisition is unprofitable**, driving high refund losses.  
- **PayPal users experience the most friction**, leading to cancellations.  
- **Customer data quality is critically low**, limiting retention and segmentation.  
- **Instagram and Email are the most reliable revenue channels** and should be prioritized.

---

## **Next Steps**

- Improve fulfilment processes to reduce pending and cancelled orders.  
- Reassess Facebook targeting and creative to reduce refund‑driven losses.  
- Strengthen email capture and validation at checkout.  
- Introduce channel‑specific refund and cancellation monitoring.  
- Expand dataset to include repeat behavior and customer lifetime value (CLV).  
- Add forecasting models for sales and operational load.
- further analysis required to dive deeper into customer behavior, marketing spend, and conversion rate (CVR)

---

## **Repository Structure**

```
ecommerce-project/
│
├── data/
│   ├── power_query_relay_dataset1.csv
│   ├── power_query_relay_dataset2.csv
│   ├── power_query_relay_dataset3.csv
│   └── cleaned_orders.csv
│
├── sql/
│   ├── 01_combine_tables.sql
│   ├── 02_standardize_columns.sql
│   ├── 03_clean_types.sql
│   ├── 04_clean_emails.sql
│   ├── 05_clean_country.sql
│   ├── 06_clean_status.sql
│   ├── 07_product_category_fix.sql
│   └── 08_remove_duplicates.sql
│
├── DAX measures.md/
│  
│
├── powerbi/
│   └── ecommerce_dashboard.pbix
│
└── README.md
```
