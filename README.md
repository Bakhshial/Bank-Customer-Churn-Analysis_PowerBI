# Bank-Customer-Churn-Analysis_PowerBI

This repository contains the complete workflow and documentation for analyzing bank customer churn using Power BI. The project aims to identify factors contributing to customer attrition and develop strategies for improving customer retention.

## Table of Contents
    Project Overview
    Business Requirement Document (BRD)
    Functional Requirement Document (FRD)
    Data Gathering
    Data Cleaning / Data Transformation
    Data Modeling
    UI Creation
    DAX Functions
    Enhance UI
    Row-Level Security (RLS)
    Workspace Management
    Publishing Reports
    Dashboard/Mobile View Creation
    Gateway Setup
    Data Refresh Scheduling
    Role-Based Security
    Managing Alerts and Subscriptions
    Sharing Reports
    Key Performance Indicators (KPIs)
    Filters
    Charts
    Challenges
    Interview Questions
    DAX Measures and Columns
    Insights
## Project Overview
The objective of this project is to analyze customer churn data from a bank to identify patterns and factors contributing to customer attrition. By understanding these factors, the bank can implement strategies to improve customer retention and loyalty.

## Business Requirement Document (BRD)
The BRD outlines the data dictionary and the purpose of each data field, the data gathering process, and the overall goals for the churn analysis.

## Functional Requirement Document (FRD)
The FRD provides detailed requirements for data gathering, transformation, modeling, and visualization using Power BI.

## Data Gathering
Data is gathered from multiple sources including Excel, CSV files, and MySQL server. The relevant data assets include:

    ActiveCustomer
    Bank_Churn
    CreditCard
    CustomerInfo
    ExitCustomer
    Gender
    Geography
### Data Cleaning / Data Transformation
Data cleaning and transformation processes are applied to ensure data quality and consistency. This includes handling missing values, data type conversions, and creating calculated columns.

## Data Modeling
Data modeling involves creating relationships between different data tables to build a cohesive data model in Power BI.

## UI Creation
The user interface is created using Power BI's visualization tools to build interactive reports and dashboards.

## DAX Functions
DAX functions are used to create calculated columns and measures for data analysis. Key measures include Active Customers, Total Customers, Inactive Customers, Credit Card Holders, Non-Credit Card Holders, Exit Customers, Retain Customers, and Churn Percentage.

## Enhance UI
Enhancements to the UI include custom visuals, formatting, and user-friendly navigation.

## Row-Level Security (RLS)
RLS is implemented to ensure that users can only access data relevant to their roles.

## Workspace Management
Workspaces are created in Power BI to manage and share reports with relevant stakeholders.

## Publishing Reports
Reports are published to the Power BI service for access and distribution.

## Dashboard/Mobile View Creation
Dashboards and mobile views are created to provide a comprehensive view of the data on different devices.

## Gateway Setup
A data gateway is set up to enable scheduled data refreshes.

## Data Refresh Scheduling
Data refresh schedules are configured to ensure that reports are updated with the latest data.

## Role-Based Security
Roles are added to security settings to manage user access and permissions.

## Managing Alerts and Subscriptions
Alerts and subscriptions are set up to notify users of important changes and updates.

## Sharing Reports
Reports are shared with stakeholders through Power BI's sharing features.

## Key Performance Indicators (KPIs)
The following KPIs are tracked:

    Total Customers: 100,000
    Active Customers: 5,151
    Inactive Customers: 4,849
    Credit Card Holders: 7,055
    Non-Credit Card Holders: 2,945
    Exit Customers: 2,037
    Retain Customers: 7,963
## Filters
Filters are applied to analyze data by:

    Year
    Month
    Location
    Active Status
    Exit Status
    Gender
## Charts
The following charts are created:

    Bar chart: Year and month on the x-axis, total customers on the y-axis, and legend for active category.
    Line chart: Month on the x-axis, exit customers on the y-axis, and previous month customers on the second y-axis.
    Pie chart: Total customers by gender.
    Bar chart: Total customers by credit type.
    Pie charts: Various categories.
    
## Challenges
    Bookmarks
    Bookmark navigators not working
    Left and right buttons not working
## Interview Questions
    Difference between import mode and direct query mode in Power BI.
    Types of transformations done in Power BI.
    Data modeling in Power BI.
    Types of schemas worked with in Power BI.
    Types and differences of RLS in Power BI.
    How to refresh data in Power BI.
    Frequency of scheduled refresh.
    Purpose of using gateways.
    Difference between dashboards and reports.
    Why slicers are not pinned in dashboards.
    Need for managing alerts.
## DAX Measures and Columns
#### Measures
    Active Customers = CALCULATE(COUNT(Bank_Churn[CustomerId]), ActiveCustomer[ActiveCategory] = "Active Member")
    Total Customers = COUNT(Bank_Churn[CustomerId])
    Inactive Customers = [Total Customers] - [Active Customers]
    Inactive Customers = CALCULATE(COUNT(Bank_Churn[CustomerId]), ActiveCustomer[ActiveCategory] = "Inactive Member")
    Credit Card Holders = CALCULATE(COUNT(Bank_Churn[CustomerId]), 'CreditCard'[Category] = "credit card holder")
    Non-Credit Card Holders = CALCULATE(COUNT(Bank_Churn[CustomerId]), 'CreditCard'[Category] = "non credit card holder")
    Exit Customers = CALCULATE([Total Customers], 'ExitCustomer'[ExitCategory] = "Exit")
    Retain Customers = CALCULATE([Total Customers], 'ExitCustomer'[ExitCategory] = "Retain")
    Previous Month = CALCULATE([Exit Customers], PREVIOUSMONTH(Datemaster[Date]))
    Churn % = VAR EC = [Exit Customers] VAR TC = [Total Customers] VAR Churnpect = DIVIDE(EC, TC) RETURN Churnpect
#### Columns
    Credit Type = SWITCH(TRUE(), Bank_Churn[CreditScore] >= 800 && Bank_Churn[CreditScore] <= 850, "Excellent", Bank_Churn[CreditScore] >= 740 && Bank_Churn[CreditScore] <= 799, "Very Good", Bank_Churn[CreditScore] >= 670 && Bank_Churn[CreditScore] <= 739, "Good", Bank_Churn[CreditScore] >= 580 && Bank_Churn[CreditScore] <= 669, "Fair", Bank_Churn[CreditScore] >= 300 && Bank_Churn[CreditScore] <= 579, "Poor")
## Insights
Identified patterns and key indicators of customer churn.
Developed strategies for customer retention and loyalty programs.
