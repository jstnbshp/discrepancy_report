---

# Advertising Data Comparison and Discrepancy Reporting

## Introduction

This project aims to develop a system that compares digital advertising impression data from ad servers and pixel data to identify discrepancies. The primary objective is to calculate the percentage difference in total impressions for different creative IDs across multiple days and generate a detailed report. The system is initially developed and tested using Google Colab, with plans for migration to a production environment.

## Objectives

- **Data Ingestion**: Load ad server and pixel data into the system.
- **Data Preprocessing**: Clean and standardize ad server data.
- **Metadata Integration**: Enrich creative IDs with metadata using a Language Model (LLM).
- **Data Aggregation**: Sum impressions by creative ID.
- **Comparison and Discrepancy Identification**: Calculate differences and percentage discrepancies between datasets.
- **Reporting**: Generate and save a detailed report as an Excel file with multiple sheets.

## Functional Requirements

### Data Ingestion
- Upload CSV files for ad server and pixel data.
- Gracefully handle errors in file uploads.
- Skip metadata headers in ad server data.

### Data Preprocessing
- Standardize date formats.
- Clean and normalize creative IDs.
- Handle missing values with appropriate defaults (e.g., zero for impressions).

### Metadata Integration
- Enrich creative IDs with metadata attributes (e.g., advertisement type, category) using an LLM or mock function.
- Use a source file to map known terminology and issues, integrating this data into the discrepancy report.

### Data Aggregation
- Aggregate data by summing impressions for each creative ID.

### Comparison and Discrepancy Identification
- Merge aggregated datasets on creative ID.
- Calculate absolute and percentage differences in impressions.
- Format percentage differences to two decimal places.

### Reporting
- Generate a report with discrepancies and save it as an Excel file with separate sheets for discrepancies, pixel data, and ad server data.
- Format the Excel file for easy viewing in applications like Microsoft Excel.

## Differences Between SQL and Python for This Task

### SQL
- **Advantages**: Efficient data handling, aggregation, and filtering within databases.
- **Limitations**: Less flexibility and readability for complex data manipulations.

### Python
- **Advantages**: Suited for complex data processing, integration, and visualization. Extensive libraries for machine learning and analytics.
- **Limitations**: Slower performance for very large datasets and requires a more complex setup.

## Test Plan

### Testing in SQL
- **Data Preparation**: Create tables, insert test data.
- **Data Preprocessing**: Write SQL queries for data cleaning.
- **Data Aggregation**: Sum impressions by creative ID using SQL queries.
- **Comparison and Reporting**: Calculate discrepancies and generate reports using SQL.

### Testing in Python
- **Data Preparation**: Load data into pandas DataFrames.
- **Data Preprocessing**: Use pandas for data cleaning.
- **Data Aggregation**: Sum impressions by creative ID using pandas.
- **Comparison and Reporting**: Calculate discrepancies and generate Excel reports using pandas and openpyxl.

## Milestones

- **Week 1**: Set up the Google Colab environment; implement data ingestion and preprocessing.
- **Week 2**: Integrate metadata enrichment; implement data aggregation logic.
- **Week 3**: Develop comparison and discrepancy identification logic.
- **Week 4**: Generate the Excel report; conduct testing.
- **Week 5**: Review and refine the system; prepare for production migration.

## Stakeholders

- **Project Manager**: Oversees the project timeline and deliverables.
- **Data Analysts**: Use the system to compare and analyze advertising data.
- **Developers**: Implement the system functionalities.
- **IT Security**: Ensure data security and compliance.
- **End Users**: Upload data and review reports.

## Appendix

- **Sample Data Files**: Examples of ad server and pixel data CSV files for testing.
- **Metadata Mapping**: Documentation on attributes added to creative IDs via the LLM.
- **Technical Specifications**: Detailed documentation on preprocessing, aggregation, and comparison algorithms.

## Approval

- **Project Sponsor**: [Name]
- **Date**: [Date]

---
