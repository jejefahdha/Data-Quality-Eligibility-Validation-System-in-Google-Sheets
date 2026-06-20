# Data Quality and Eligibility Validation System in Google Sheets
Google Sheets-based system for data collection, validation, and automated eligibility assessment using structured data quality rules and business logic.

# Overview
This project demonstrates the design of a standardized online data collection template using Google Sheets to improve data quality, streamline beneficiary registration, and reduce manual processing for the Tobacco Excise Revenue Sharing Fund (DBH CHT) beneficiary program.
The solution transforms a fragmented, spreadsheet-based workflow into a centralized data collection system with built-in validation rules, automated consolidation, and standardized data entry.

# Business Problem
The annual beneficiary registration process for the Tobacco Excise Revenue Sharing Fund (DBH CHT) was previously conducted using separate Microsoft Excel files distributed to the Human Resources (HR) department of each participating factory.
After submission, all individual files were manually consolidated into a master spreadsheet. This process introduced several data quality challenges, including:
- Manual consolidation or merging errors between individual files and the master dataset
- Missing or incomplete information during the merging process
- Duplicate beneficiary records
- Inconsistent data formats across factories
- Difficulty applying and validating eligibility rules, such as age requirements, employment duration, and multiple-factory employment
- Time consuming updates, as changes submitted by individual factories also required manual synchronization in the master dataset
These challenges increased the workload for administrators while making it difficult to maintain an accurate and consistent beneficiary database.

# Solution
To address these challenges, I designed a centralized Google Sheets-based data collection system that standardizes data entry while reducing manual processing.
Key improvements include:
- Replacing offline spreadsheets with online data entry forms for each factory
- Automatically consolidating individual factory submissions into a centralized master dataset
- Enabling real-time monitoring of submission progress and data updates
- Separating responsibilities by allowing HR personnel to focus solely on beneficiary data entry while applying validation and eligibility rules within the centralized master dataset
- Reducing manual reconciliation by ensuring updates from individual factory sheets are automatically reflected in the master dataset
- Automating data transformation processes, including extraction of date of birth from NIK and age calculation based on a defined cutoff date in the master dataset
- Implementing business rule–based eligibility assessment, including age filtering (18–65 years) and detection of multiple-factory employment
- Generating a standardized eligibility output status (Eligible / Not Eligible / Requires Review) to support decision-making and reporting

# Preview
**Master Sheet**

<img width="1709" height="984" alt="image" src="https://github.com/user-attachments/assets/2d9aeaab-6d72-4a57-bdaf-d9f4414d855c" />
.

**Entry Sheet**

<img width="1709" height="984" alt="image" src="https://github.com/user-attachments/assets/a274e47f-ecd6-41f5-b617-b13298b6dd66" />

# Validation Rules
## HR Data Entry Sheet (by Factory)
To improve data quality at the point of entry, the template incorporates multiple validation mechanisms.
1. Required Field Validation
   Mandatory fields are highlighted in yellow when left blank.
2. Invalid Data Detection
   Cells containing values that do not meet validation requirements are highlighted in red.
3. Format Validation
   The form validates data formats for key identification fields, including:
   - National Identification Number (NIK): numeric, exactly 16 digits
   - Family Card Number (No. KK): numeric, exactly 16 digits
   - RT and RW: numeric, exactly 3 digits
4. Standardized Reference Values
   Administrative area fields (Kelurahan and Kecamatan) are provided as predefined dropdown lists to ensure consistent naming across all submissions.
Users may copy and paste values from external sources, provided the text exactly matches one of the available options. Letter casing is ignored during validation.
## Master Sheet
In addition to consolidating data from all factory entry sheets, the master sheet performs a second layer of validation and automatically applies business rules to determine beneficiary eligibility.
The master sheet includes the following processes:
1. Secondary Validation
   Applies the same validation rules used in the HR Entry Sheet as a second quality assurance check. Flags missing, invalid, or inconsistent values that may have bypassed initial data entry.
2. Automated Calculations
   The system automatically derives additional information required for eligibility assessment, including:
   - Date of Birth Extraction: Extracts the beneficiary's date of birth from the National Identification Number (NIK).
   - Age Calculation: Calculates the beneficiary's age based on a configurable cutoff date determined by the government authority administering the social assistance program. 
   - Multiple Factory Employment Check: Identifies individuals who are registered by more than one participating factory.
3. Eligibility Assessment
Based on the validation and calculated fields, the system automatically determines whether each candidate beneficiary is eligible.
A beneficiary is considered Eligible only if all of the following conditions are met:
  - All required information is valid.
  - The beneficiary is between 18 and 65 years old (inclusive) on the specified cutoff date.
  - The beneficiary is registered under only one factory.
Records that do not satisfy one or more conditions are automatically flagged for further review.

# Skills Demonstrated
- Data Validation
- Conditional Formatting
- Array Formulas
- Google Apps Script
- Data Cleaning, Standardization, and Transformation
- Business Rule Implementation
- Data Quality Assurance
- Duplicate Detection
- Data Consolidation
- Spreadsheet Process Automation

# Future Improvements
While Google Sheets significantly improves the existing workflow, a dedicated web application would provide a more scalable and maintainable long-term solution.
A future system could introduce role-based access for:
- System Administrator
- Program Staff
- Factory HR
- Beneficiaries
Potential enhancements include:
- Automated eligibility validation based on configurable business rules
- Beneficiary portal for application status tracking
- Digital document submission and verification
- Direct integration with banking systems for beneficiary payment processing
- Standardized data export aligned with bank requirements, or API integration where available to eliminate duplicate data submission

# Google Sheets
🔗 View Google Sheets Template: [(Click Here)](https://docs.google.com/spreadsheets/d/196nSnYkkjTwYRGH2hK8LgrqmdxZPyvNDtJYhe0m7fkE/edit?gid=1433855594#gid=1433855594)

**Note:** _This portfolio version uses fictional sample data. The original template was developed for a government beneficiary registration program and has been recreated with anonymized data to protect confidential information while preserving the workflow, validation logic, and automation features._
