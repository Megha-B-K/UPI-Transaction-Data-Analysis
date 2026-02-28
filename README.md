# Power BI UPI Transaction Analysis Dashboard 💳🇮🇳

**Author**: Megha Kallapur  
**Location**: Karnataka, India  
**[GitHub](https://github.com/Megha-B-K)**

---

## Project Overview

Interactive **Power BI dashboard** analyzing **UPI remittances & transactions** across **Bank, City, Gender, Month, Year**. Perfect for fintech analysis, fraud detection, and digital payment trends.

**Dataset**: UPI transaction records with Balance Amount, Transaction Amount by demographics and time periods.

**Business Value**: Track remittance patterns, identify high-volume months/banks/cities, analyze gender-based trends.

---

## ashboard Features

| Visual Type         | Key Metrics                | Insights                        |
|---------------------|----------------------------|---------------------------------|
| **Matrix Table**    | Balance/Transaction Amount | By Bank, City, Gender, Month    |
| **Column Chart**    | Remittance Balance         | Monthly trends (Jan-Dec by Year)|
| **Filters/Slicers** | Bank, City, Gender, Date   | Dynamic interactivity           | 
| **Totals**          | Overall UPI Volume         | Cross-tab analysis              |

---

## Technical Implementation

### Data Model
Fact Tables:
├── Balance Amount (by Bank/City/Gender/Month)
└── Transaction Amount

Dimensions: Bank, City, Gender, Date (Month/Year)

Relationships: Many-to-One on Bank, City, Gender, Month

### Key DAX Measures
```dax
-- Total Remittance Balance
Total Remittance = SUM('UPI Data'[Balance Amount])

-- Avg Transaction per Bank
Avg Tx per Bank = 
AVERAGEX(
    VALUES('UPI Data'[Bank]),
    CALCULATE(SUM('UPI Data'[Transaction Amount]))
)

-- YoY Growth
YoY Remittance Growth = 
DIVIDE(
    [Total Remittance] - CALCULATE([Total Remittance], SAMEPERIODLASTYEAR('Date'[Date])),
    CALCULATE([Total Remittance], SAMEPERIODLASTYEAR('Date'[Date]))
)

-- Gender-wise %
Remittance % by Gender = 
DIVIDE([Total Remittance], CALCULATE([Total Remittance], ALL('UPI Data'[Gender])), 0)

### Actionable Insights
Monthly Peaks: Highest remittances in peak months (visible in column charts)

Bank Leaders: Top banks by balance/transaction volume

City Hotspots: Urban vs rural remittance patterns

Gender Trends: Transaction behavior differences

Yearly Growth: UPI adoption acceleration [web:26][web:34]

Gmail: meghakallapur@gmail.com
Last Updated: February 2026 [cite:11]
