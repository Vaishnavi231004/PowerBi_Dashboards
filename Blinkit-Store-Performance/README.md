# **Blinkit Store Performance & Product Insights Dashboard**

## **Project Overview**
This project showcases an **interactive Power BI dashboard** designed to analyze **Blinkit’s store performance and product-level insights**.  
The dashboard transforms **raw retail data** into **actionable business insights** using **Power Query**, **DAX**, and **effective visual storytelling**.

---

## **Key Focus Areas**
- **Sales performance** across products and outlets  
- Impact of **outlet location, size, and age** on sales  
- **Product characteristics** such as **visibility, weight, and ratings**

---

## **Dataset Summary**

| **Column** | **Description** |
|-----------|----------------|
| **Item Fat Content** | Low Fat / Regular |
| **Item Identifier** | Unique product code |
| **Item Type** | Food, Soft Drinks, Household, etc. |
| **Outlet Establishment Year** | Year the outlet was opened |
| **Outlet Identifier** | Store code |
| **Outlet Location Type** | Tier 1 / Tier 2 / Tier 3 |
| **Outlet Size** | Small / Medium / High |
| **Outlet Type** | Grocery Store / Supermarket |
| **Item Visibility** | Shelf visibility percentage |
| **Item Weight** | Weight of item |
| **Sales** | Sales amount |
| **Rating** | Customer rating |

---

## **Data Transformation & Feature Engineering**

### **Data Cleaning (Power Query)**
- Removed **duplicate records**
- Trimmed and cleaned **column names**
- Standardized **inconsistent values**
  - `low fat`, `LF`, `Low Fat` → **Low Fat**
  - `reg`, `Regular` → **Regular**
- Handled **missing values**
  - **Item Weight** replaced with **average by Item Type**
  - **Item Visibility** replaced with **0 or median value**

---

### **Feature Engineering**
- **Item Age**

Item Age = Current Year − Outlet Establishment Year


- **Sales Category**
- **High Sales** (> 2000)
- **Medium Sales** (500–2000)
- **Low Sales** (< 500)

- Extracted **Item Category Code** from **Item Identifier**

- **Aggregated Metrics**
- **Average Sales by Outlet**
- **Average Weight by Item Type**

---

## **Key DAX Measures**

```DAX
Total Sales = SUM(Data[Sales])
Avg Sales = AVERAGE(Data[Sales])
Item Count = DISTINCTCOUNT(Data[Item Identifier])
Avg Rating = AVERAGE(Data[Rating])

Outlet Age = YEAR(TODAY()) - AVERAGE(Data[Outlet Establishment Year])
Avg Visibility = AVERAGE(Data[Item Visibility])
Avg Weight = AVERAGE(Data[Item Weight])

LowFat Sales =
CALCULATE([Total Sales], Data[Item Fat Content] = "Low Fat")

Regular Sales =
CALCULATE([Total Sales], Data[Item Fat Content] = "Regular")


## **Dashboard Sections & Insights**

### **Sales Performance Insights**
<p align="center">
  <img src="screenshots/Sales Performance Insights.png" width="800"/>
  <br/>
  <em>Sales distribution by item type, fat content, and outlet characteristics</em>
</p>

**Business Questions Answered**
- Which **item types** generate the **highest revenue**?
- Do **Low Fat** or **Regular** items perform better?

---

### **Outlet Analysis**
<p align="center">
  <img src="screenshots/Outlet Analysis.png" width="800"/>
  <br/>
  <em>Sales comparison across outlet tiers, identifiers, and establishment years</em>
</p>

**Business Questions Answered**
- Which **outlet tier** performs best?
- Does **outlet age** affect **sales performance**?

---

### **Product Characteristics**
<p align="center">
  <img src="screenshots/Product Characteristics.png" width="800"/>
  <br/>
  <em>Relationship between item visibility, sales, weight, and ratings</em>
</p>

**Business Questions Answered**
- Does **higher visibility** lead to **higher sales**?
- Which **product categories** receive **better ratings**?

---

### **KPI Scorecards**
<p align="center">
  <img src="screenshots/KPI Scorecards.png" width="800"/>
  <br/>
  <em>Key performance indicators highlighting top and low-performing entities</em>
</p>

**KPIs Included**
- **Highest Selling Item**
- **Best Performing Outlet**
- **Lowest Rated Outlet**
- **Sales per Outlet Type**

---

## **Tools & Technologies**
- **Power BI Desktop**
- **Power Query**
- **DAX**
- **Data Modeling and Visualization**

---

## **Key Learnings**
- **End-to-end data cleaning and transformation**
- Writing **business-focused DAX measures**
- Designing **insight-driven dashboards**
- Translating data into **clear business narratives**

---

## **Author**
**Vaishnavi Mohite**  
**Power BI | Data Visualization**
