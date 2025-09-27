# Bank Customer Churn Analysis of RBC Bank

<p align="center">
<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/b9bcabca-ebf0-410e-ab4f-98d510794cf7" />
</p>

<p align="center">
![Power BI Logo](https://img.shields.io/badge/PowerBI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
</p>

## Overview:

This project demonstrates my Power BI and DAX problem-solving skills through the analysis of customer churn data for a banking institution. The project involves setting up the data model, transforming raw Excel data into a structured star schema, creating complex DAX measures, and building interactive dashboards that provide actionable insights for customer retention strategies.

<p align="center">
<img width="1430" height="797" alt="image" src="https://github.com/user-attachments/assets/8d3a4d47-d77e-4356-bda7-fb2b558a90e6" />
</p>

## Project Structure:

- **Data Transformation:** Converting raw Excel data into fact and dimension tables using Power Query Editor
- **Data Modeling:** Creating relationships between fact and dimension tables in a star schema
- **DAX Measures:** Developing 9 custom measures for comprehensive churn analysis
- **Dashboard Design:** Building interactive visualizations with optimized performance using Figma backgrounds
- **Business Intelligence:** Generating insights and actionable recommendations for stakeholder decision-making

## Data Model Structure:

<p align="center">
<img width="1211" height="753" alt="image" src="https://github.com/user-attachments/assets/282f6664-ee49-4f56-a5e6-80145400fb43" />
</p>

```
Fact Table: Bank_Churn
Dimension Tables:
├── Dim-ActiveCustomer
├── Dim-CreditCard  
├── Dim-CustomerInfo
├── Dim-ExitCustomer
├── Dim-Gender
├── Dim-Geography
└── DateMaster
```

## Data Transformation Process:

**Original Data:** Single Excel file (Bank_Churn.xlsx) containing all customer information

**Transformation Steps:**
1. Loaded data into Power Query Editor
2. Split data into logical dimension tables for better performance
3. Created relationships between fact and dimension tables
4. Established date master table for time intelligence
5. Optimized data types and removed unnecessary columns

## DAX Measures Created:

### Core Customer Metric
```dax
Total Customers = COUNT('Fact-Bank_Churn'[CustomerId])

Active Customers = CALCULATE(COUNT('Fact-Bank_Churn'[CustomerId]),
                            'Dim-ActiveCustomer'[ActiveCategory] = "ACTIVE MEMBER")

InActive Customers = CALCULATE(COUNT('Fact-Bank_Churn'[CustomerId]), 
                              'Dim-ActiveCustomer'[ActiveCategory] = "Inactive Member")

Exit Customers = CALCULATE(COUNT('Fact-Bank_Churn'[CustomerId]),
                          'Dim-ExitCustomer'[ExitCategory] = "EXIT")

Retain Customers = CALCULATE(COUNT('Fact-Bank_Churn'[CustomerId]),
                            'Dim-ExitCustomer'[ExitCategory] = "Retain")
```

### Advanced Analytics
```dax
Churn % = 
VAR Exit_Customers = [Exit Customers]
VAR Total_Customers = [Total Customers]
VAR Churn_per = DIVIDE(Exit_Customers, Total_Customers)
RETURN Churn_per

Previous_Month_ExitCustomers = CALCULATE([Exit Customers],
                                        PREVIOUSMONTH(DateMaster[Date]))
```

### Credit Card Segmentation
```dax
Credit Card Holders = CALCULATE(COUNT('Fact-Bank_Churn'[CustomerId]), 
                               'Dim-CreditCard'[Category] = "Credit Card Holder")

Non Credit Card Holders = CALCULATE(COUNT('Fact-Bank_Churn'[CustomerId]),
                                   'Dim-CreditCard'[Category] = "Non Credit Card Holder")
```

## Performance Optimization:

- **Custom Backgrounds:** Used Figma to design dashboard backgrounds, reducing Power BI file size and improving load times
- **Star Schema:** Implemented proper data modeling for optimal query performance  
- **Efficient DAX:** Used CALCULATE and context transition for better measure performance
- **Relationship Optimization:** Created proper one-to-many relationships between dimensions and fact table

## Key Dashboard Features:

### Executive Summary
- **10,000** Total Customers tracked
- **7,963** Retain Customers (79.63% retention rate)
- **2,037** Exit Customers (20.37% churn rate)
- **7,055** Credit Card Holders vs **2,945** Non Credit Card Holders

### Interactive Analytics
- Customer activity trends over time (2016-2019)
- Geographic distribution analysis across France, Germany, and Spain
- Credit card holder vs non-holder churn patterns
- Monthly churn tracking with previous month comparisons
- Exit customer segmentation by credit score categories

## Project Dashboard Views:

### Home Page
<p align="center">
<img width="1430" height="797" alt="image" src="https://github.com/user-attachments/assets/501891e6-f01d-4a66-916f-4e02b97e7aa5" />
</p>

### Slicer Selection
<p align="center">
<img width="1434" height="800" alt="image" src="https://github.com/user-attachments/assets/f7eb0856-a235-42c3-835b-9e4fc903a0e6" />
</p>

### RLS Security Feature
<p align="center">
<img width="1053" height="619" alt="image" src="https://github.com/user-attachments/assets/b35fb28b-1a53-4934-aacf-5918f63c1a41" />
</p>

<p align="center">
<img width="377" height="381" alt="image" src="https://github.com/user-attachments/assets/cf8a9a12-f588-4ccd-9a49-de578515bebf" />
</p>

## Key Insights:

**Churn Patterns:** 20.37% overall churn rate with clear differences between credit card holders and non-holders

**Geographic Trends:** Spain shows highest customer concentration (50.14%) followed by France (25.09%) and Germany (24.77%)

**Credit Impact:** Significant churn rate differences between credit card holders (69.91%) and non-holders (30.09%)

**Temporal Analysis:** Monthly churn tracking reveals seasonal patterns and trend identification opportunities

**Risk Segmentation:** Clear categorization of customers by credit score (Excellent, Very Good, Good, Fair, Poor)

## Business Recommendations:

**Targeted Retention Programs:** Focus retention efforts on high-risk segments identified through credit score and activity patterns

**Geographic Strategy:** Develop region-specific retention campaigns, especially in high-churn areas

**Credit Card Promotion:** Encourage credit card adoption as holders show different engagement patterns

**Early Warning System:** Implement alerts for customers showing early churn indicators (inactive status, declining activity)

**Seasonal Campaigns:** Launch targeted campaigns during months showing historically higher churn rates

**Customer Segmentation:** Create personalized retention strategies based on credit score categories and demographics

## Technical Skills Demonstrated:

- **Power BI:** Dashboard design, data visualization, performance optimization
- **DAX:** Complex measure creation, time intelligence, context manipulation
- **Power Query:** Data transformation, ETL processes, relationship modeling
- **Data Modeling:** Star schema design, relationship optimization
- **UI/UX Design:** Custom background creation using Figma for enhanced user experience
- **Business Analysis:** Translating data insights into actionable business recommendations

## Future Enhancements:

- Implement predictive churn modeling using Power BI AI features
- Add real-time data refresh capabilities
- Create automated alert system for high-risk customers  
- Develop cohort analysis for customer lifecycle understanding
- Integrate external economic indicators for enhanced analysis

## Project Impact:

This analysis enables banks to:
- **Identify at-risk customers** before they churn using predictive insights
- **Optimize retention budget allocation** by focusing on high-value segments
- **Track retention campaign effectiveness** through month-over-month comparisons  
- **Reduce customer acquisition costs** by improving retention rates
- **Increase customer lifetime value** through targeted engagement strategies

## Dashboard Structure:
```
├── Executive Summary Dashboard
├── Customer Segmentation Analysis  
├── Geographic Distribution View
├── Churn Trend Analysis
├── Credit Score Impact Assessment
└── Monthly Performance Tracking
```

## Tools & Technologies:

- **Microsoft Power BI** - Primary BI tool for dashboard creation
- **Power Query Editor** - Data transformation and modeling
- **DAX (Data Analysis Expressions)** - Custom calculations and measures  
- **Figma** - Custom background design for performance optimization
- **Excel** - Source data format and initial analysis

## Conclusion

This project showcases my ability to transform raw banking data into actionable business intelligence. The comprehensive approach demonstrates skills in data modeling, advanced DAX programming, dashboard design, and business analysis - essential capabilities for driving data-informed decisions in the financial services sector.

## Notice 
All customer data used in this project is for demonstration purposes only. The dataset represents fictional customer information and does not contain any real banking customer data. This project is solely for learning and portfolio demonstration purposes.
