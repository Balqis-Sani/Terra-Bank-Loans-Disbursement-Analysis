# Terra Bank Loans Disbursement Analysis

### Project Overview
---
This project conducted an in-depth analysis of loans disbursed by Terra Bank from 2010-20111, aiming to identify significant trends and insights related to various aspects of lending during that period. It explored customer demographics to understand the profiles of borrowers.
![Bank Loan Report](https://github.com/user-attachments/assets/6734c373-d596-4638-9e54-4aba587e9350)


### Tools
---
- Microsoft Excel - Data Cleaning
- PostgreSQL- Data Analysis
- Power BI -  Data Visualisation

### Data Cleaning / Preparation 
---
In the data preparation phase, the following tasks were performed:
- Loading the dataset
- Inspecting the datset for data quality issues
- Handling missing values
- Removing Duplicates
- Loading data into PostgreSQL for analysis
- Loadng data into Power BI for visualisation


### Exploratory Data Analysis
---
EDA involved exploring the dataset to answer the following questions:
- What was the total number of debtors and the total loaned amount yearly?
- What was the average interest by grade and by year?
- What was the breakdown of the total loaned amount by term, grade and state?
- What was the percentage of loans that were verified, unverified and source verified?
- What is the detailed information of each debtor including annual income, employment title, grade, loaned amount, funded amount, interest rate, loan status, and verification status?
- What services took up the most expenses?

### Data Analysis
---
Some interesting SQLcodes worked with in PostgreSQL include :

``` SQL
SELECT
    grade,
    issue_year,
    ROUND(AVG(interest_rate), 2) AS avg_interest_rate
FROM loan_data
GROUP BY grade, issue_year
ORDER BY issue_year, grade;
```
```SQL
SELECT
    term,
    grade,
    state,
    SUM(loan_amount) AS total_loaned
FROM loan_data
GROUP BY term, grade, state
ORDER BY total_loaned DESC;
```
```SQL
SELECT
    verification_status,
    COUNT(*) * 100.0 / (SELECT COUNT(*) FROM loan_data) AS percentage
FROM loan_data
GROUP BY verification_status;
```
```SQL
SELECT
    annual_income,
    employment_title,
    grade,
    loan_amount,
    funded_amount,
    interest_rate,
    loan_status,
    verification_status
FROM loan_data;
```

### Results/Findings
---
1. In 2011, the highest loan amount of $206,506,575 was disbursed, while the lowest loan amount of $2,219,275 was issued in the year 200. This explains why 2011 had the highest number of debtors 
(21,656), compared to only 21 in 200.
2.  Grade G loans received the highest interest rate of 21.40%, while Grade A loans had the lowest at 7.34%.
3. Canada recorded the highest total loan amount of $80 million and also had the largest number of debtors, totaling 7,099.
4. Grade B received the highest loan amount of $134 million, whereas Grade G had the lowest, with only $6 million disbursed, which may be attributed to its high interest rate of 21.40%. The high cost of borrowing could have discouraged applicants, while lenders may have also restricted loan amounts due to higher default risks.
5. Loans with a 60-month term had a higher average interest rate (14.81%) compared to 36-month loans, which had a lower rate of 11%.
6. A total of 32,950 debtors fully repaid their loans, 5,627 loans were charged off, and 1,140 remain in current status.
7. Among all debtors, 16,921 loans were verified, 12,809 were not verified, and 9,987 were source-verified.
 
### Recommendations
---

1. Analyze what factors led to the high loan disbursement in 2011 (e.g., economic policies, lower interest rates, or increased lender confidence). If favorable, consider replicating 
those strategies to boost lending in future years.

2. Consider adjusting interest rates for Grade G to make loans more attractive while balancing risk. Offering incentives like collateral-backed loans or gradual rate reductions for 
on-time payments may help increase borrowing.

3. Investigate what made Canada a top-performing region—whether due to favorable loan policies, economic conditions, or borrower creditworthiness. If possible, apply similar 
strategies in lower-performing regions.

4. Assess why Grade B is preferred and use similar risk assessment models for lower grades. Offering customized repayment plans for Grade G borrowers may encourage more 
lending while managing risk.

5. To encourage longer-term borrowing, consider reducing interest rates slightly for 60-month loans or offering incentives like lower monthly payments to make them more 
attractive.

6. Identify patterns in charged-off loans (e.g., borrower profiles, loan terms) and implement stronger risk assessment or early intervention strategies (e.g., automated payment 
reminders, restructuring options) to reduce defaults.

7. Strengthen the verification process to reduce the number of unverified loans, which could pose higher risks. Encouraging source verification may improve lender confidence 
and reduce default rates

