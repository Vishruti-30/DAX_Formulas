# 📊 Sales Analysis with Power BI & DAX

This project demonstrates how to use **Power BI** and **DAX (Data Analysis Expressions)** to build an interactive sales dashboard and generate insights through custom measures.

## 🔍 Objective
To explore sales performance across products, regions, and time using DAX formulas. The project aims to transform raw sales data into clear business metrics such as total sales, average unit price, and year-over-year sales growth.

## 📊 Dataset
- Source: Mock dataset created manually
- Features: `Date`, `Region`, `Product`, `Salesperson`, `Units Sold`, `Unit Price`, `Total Sales`
- Size: 100+ rows representing fictional sales transactions

## 🛠️ Tools & Technologies
- **Power BI Desktop**
- **DAX** for custom metrics and calculated measures
- **Slicers, Cards, Line & Bar Charts** for interactive visualizations

## 📈 Visualizations
- **KPI Cards**: Total Sales, Average Unit Price, Sales Growth %
- **Line Chart**: Sales trends over time
- **Bar Charts**: Region-wise and Product-wise performance
- **Slicers**: Region, Product, Salesperson, and Date Range filters

## 🔢 Key DAX Measures

### Total Sales  
```DAX
**Total Sales** = SUM('Sales_Data'[Total Sales]) - Calculates total revenue across all records.

### Average Unit Price
```DAX
**Average Unit Price** = AVERAGE('Sales_Data'[Unit Price]) - Returns the average selling price per unit.

### Sales Growth %
```DAX
**Sales Growth %** = 
VAR CurrentYearSales = CALCULATE(SUM('Sales_Data'[Total Sales]), YEAR('Sales_Data'[Date]) = YEAR(TODAY()))
VAR PreviousYearSales = CALCULATE(SUM('Sales_Data'[Total Sales]), YEAR('Sales_Data'[Date]) = YEAR(TODAY()) - 1)
RETURN
IF(
    PreviousYearSales = 0,
    BLANK(),
    (CurrentYearSales - PreviousYearSales) / PreviousYearSales
) - Measures year-over-year revenue growth.
