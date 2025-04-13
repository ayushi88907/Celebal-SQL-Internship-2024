# 📊 Insignia Corporation – Data Warehouse Project
---

## 🚀 About the Project

This project was a real-time simulation of a Data Engineering and BI setup for **Insignia Corporation**, a company that has recently started selling gifts online.

I was responsible for breaking down the raw data, designing the data model, and building an end-to-end ETL pipeline using **SQL Server** — everything from creating dimension/fact tables to handling slowly changing dimensions (SCDs) and implementing lineage for data auditing.

---

## 🧱 Part 1 – Data Modeling

I started by analyzing the `Insignia_staging` table and identified the right dimensions and facts. Based on that, I created:

- `Customer_Dim` (with SCD Type 2)
- `Employee_Dim` (with SCD Type 2)
- `Geography_Dim` (with SCD Type 3 for population)
- `Product_Dim` (SCD Type 1)
- `Date_Dim` (with full calendar + fiscal year logic)
- `Sales_Fact` (central fact table)

I also created a **Lineage table** to track:
- Source system name
- ETL start & end time
- Rows processed
- Whether the load was successful

> 📌 Bonus: Date dimension includes data from 2000 to 2023, and fiscal year starts from July (as per company logic).

---

## ⚙️ Part 2 – ETL & SCD Handling

Once the model was ready, I worked on the **ETL pipeline**:

- Used `Insignia_staging_copy` to load fresh and incremental data
- Handled different SCD types:
  - Type 2 for `Customer` and `Employee`
  - Type 3 for `Geography`
  - Type 1 for others
- Made sure no dimension/fact table was truncated
- Managed **late arriving data** smoothly
- Followed proper **surrogate key generation**

And yes — I **strictly avoided MERGE statements**, used only **LEFT JOIN + UPDATE** as instructed.

---

## ✅ Reconciliation Check (Bonus)

After each ETL run, I included a mini reconciliation logic to verify the number of records in the source vs what actually got loaded into the warehouse.

---

## 🛠️ Tech & Concepts Used

- SQL Server
- Data Warehousing concepts
- SCD Types 1, 2, 3
- Surrogate Keys
- Lineage & Auditing
- ETL Best Practices

---

## 💡 What I Learned

This project helped me understand real-world challenges in data warehousing — from designing the schema to dealing with changing records, handling data quality, and tracking each load with proper logging.

I’ve not just written queries here — I’ve actually **built a full data flow** from raw input to analytics-ready data, keeping performance, accuracy, and scalability in mind.

---

## 🙌 Final Note

I really enjoyed building this solution — it gave me exposure to enterprise-level data engineering workflows. Happy to connect if you're working on similar problems or want to collaborate! 😊

