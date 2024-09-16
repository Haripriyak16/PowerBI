# Bank Loan Analysis
# Problem Statement: Key Performance Indicators (KPIs) Requirements

### Total Loan Applications
We need to calculate the total number of loan applications received during a specified period. Additionally, it is essential to monitor the Month-to-Date (MTD) Loan Applications and track changes Month-over-Month (MoM).

### Total Funded Amount
Understanding the total amount of funds disbursed as loans is crucial. We also want to keep an eye on the MTD Total Funded Amount and analyze the Month-over-Month (MoM) changes in this metric.

### Total Amount Received
Tracking the total amount received from borrowers is essential for assessing the bank's cash flow and loan repayment. We should analyze the Month-to-Date (MTD) Total Amount Received and observe the Month-over-Month (MoM) changes.

### Average Interest Rate
Calculating the average interest rate across all loans, MTD, and monitoring the Month-over-Month (MoM) variations in interest rates will provide insights into our lending portfolio's overall cost.

### Average Debt-to-Income Ratio (DTI)
Evaluating the average DTI for our borrowers helps us gauge their financial health. We need to compute the average DTI for all loans, MTD, and track Month-over-Month (MoM) fluctuations.

### Good Loan vs. Bad Loan KPIs

**Good Loan Metrics:**
- Good Loan Application Percentage
- Good Loan Applications
- Good Loan Funded Amount
- Good Loan Total Received Amount

**Bad Loan Metrics:**
- Bad Loan Percentage
- Bad Loan Applications
- Bad Loan Funded Amount
- Bad Loan Total Received Amount

### Loan Status Grid View
In order to gain a comprehensive overview of our lending operations and monitor the performance of loans, we aim to create a grid view report categorized by 'Loan Status.’ By providing insights into metrics such as 'Total Loan Applications,' 'Total Funded Amount,' 'Total Amount Received,' 'Month-to-Date (MTD) Funded Amount,' 'MTD Amount Received,' 'Average Interest Rate,' and 'Average Debt-to-Income Ratio (DTI),' this grid view will empower us to make data-driven decisions and assess the health of our loan portfolio.

### Charts and Visualizations

**Monthly Trends by Issue Date (Line Chart):**  
To identify seasonality and long-term trends in lending activities.

**Regional Analysis by State (Filled Map):**  
To identify regions with significant lending activity and assess regional disparities.

**Loan Term Analysis (Donut Chart):**  
To allow the client to understand the distribution of loans across various term lengths.

**Employee Length Analysis (Bar Chart):**  
To assess how lending metrics are distributed among borrowers with different employment lengths, helping us evaluate the impact of employment history on loan applications.

# Bank Loan Dashboard Objective and Requirements 

### Objective
To assess the performance of our lending operations through comprehensive Key Performance Indicators (KPIs). The goal is to understand various aspects of loan applications, funding, repayments, and borrower profiles. This analysis will help in making informed, data-driven decisions and optimizing the lending strategy.

### KPIs and Metrics

#### Total Loan Applications
- **Objective:** Calculate the total number of loan applications received during a specified period.
- **Requirements:**
  - Compute the total number of loan applications.
  - Track Month-to-Date (MTD) Loan Applications.
  - Monitor Month-over-Month (MoM) changes in loan applications.

#### Total Funded Amount
- **Objective:** Understand the total amount of funds disbursed as loans.
- **Requirements:**
  - Calculate the total amount funded.
  - Track the MTD Total Funded Amount.
  - Analyze MoM changes in the total funded amount.

#### Total Amount Received
- **Objective:** Track the total amount received from borrowers to assess the bank's cash flow and loan repayment.
- **Requirements:**
  - Compute the total amount received.
  - Analyze MTD Total Amount Received.
  - Observe MoM changes in the amount received.

#### Average Interest Rate
- **Objective:** Calculate the average interest rate across all loans.
- **Requirements:**
  - Compute the average interest rate.
  - Track MTD Average Interest Rate.
  - Monitor MoM variations in the interest rate.

#### Average Debt-to-Income Ratio (DTI)
- **Objective:** Evaluate the average DTI for borrowers to gauge their financial health.
- **Requirements:**
  - Calculate the average DTI across all loans.
  - Track MTD Average DTI.
  - Observe MoM fluctuations in the average DTI.

#### Good Loan vs. Bad Loan KPIs
- **Good Loan Metrics:**
  - **Good Loan Application Percentage:** Percentage of loans classified as 'Fully Paid' or 'Current.'
  - **Good Loan Applications:** Number of loans classified as 'Fully Paid' or 'Current.'
  - **Good Loan Funded Amount:** Total amount funded for loans classified as 'Fully Paid' or 'Current.'
  - **Good Loan Total Received Amount:** Total amount received from payments for loans classified as 'Fully Paid' or 'Current.'

- **Bad Loan Metrics:**
  - **Bad Loan Percentage:** Percentage of loans classified as 'Charged Off.'
  - **Bad Loan Applications:** Number of loans classified as 'Charged Off.'
  - **Bad Loan Funded Amount:** Total amount funded for loans classified as 'Charged Off.'
  - **Bad Loan Total Received Amount:** Total amount received from payments for loans classified as 'Charged Off.'

#### Loan Status Grid View
- **Objective:** Provide a comprehensive view of lending operations categorized by loan status.
- **Requirements:**
  - Display metrics such as Total Loan Applications, Total Funded Amount, Total Amount Received, MTD Funded Amount, MTD Amount Received, Average Interest Rate, and Average DTI, grouped by loan status.

### Charts and Visualizations

#### Monthly Trends by Issue Date (Line Chart)
- **Objective:** Identify seasonality and long-term trends in lending activities.

#### Regional Analysis by State (Filled Map)
- **Objective:** Assess regions with significant lending activity and identify regional disparities.

#### Loan Term Analysis (Donut Chart)
- **Objective:** Understand the distribution of loans across various term lengths.

#### Employee Length Analysis (Bar Chart)
- **Objective:** Evaluate how lending metrics are distributed among borrowers with different employment lengths, and assess the impact of employment history on loan applications.

#### Loan Purpose Breakdown (Bar Chart)
- **Objective:** Provide a visual breakdown of loan metrics based on the stated purposes of loans to understand primary reasons for seeking financing.

#### Home Ownership Analysis (Tree Map)
- **Objective:** Provide a hierarchical view of how home ownership impacts loan applications and disbursements.

**Home Ownership Analysis (Tree Map):**  
To provide a hierarchical view of how home ownership impacts loan applications and disbursements.


![Bank Dashboard](Bank%20Loan/Bank_dashboard_image_1.png)

# Bank Loan SQL Query


### Total Loan Applications
- **Objective:** Calculate the total number of loan applications received during a specified period.
- **Metrics:**
  - **Total Loan Applications**
    ```sql
    SELECT COUNT(id) as Total_Loan_Applications FROM bank_loan_data;
    ```
  - **Month-to-Date (MTD) Loan Applications**
    ```sql
    SELECT COUNT(id) as MTD_Total_Loan_Applications 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=12 AND YEAR(issue_date)=2021;
    ```
  - **Month-over-Month (MoM) Changes**
    ```sql
    SELECT COUNT(id) as PMTD_Total_Loan_Applications 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=11 AND YEAR(issue_date)=2021;
    ```

### Total Funded Amount
- **Objective:** Understand the total amount of funds disbursed as loans.
- **Metrics:**
  - **Total Funded Amount**
    ```sql
    SELECT SUM(loan_amount) as Total_Amount_Funded FROM bank_loan_data;
    ```
  - **MTD Total Funded Amount**
    ```sql
    SELECT SUM(loan_amount) as MTD_Total_Amount_Funded 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=12 AND YEAR(issue_date)=2021;
    ```
  - **Month-over-Month (MoM) Changes**
    ```sql
    SELECT SUM(loan_amount) as PMTD_Total_Amount_Funded 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=11 AND YEAR(issue_date)=2021;
    ```

### Total Amount Received
- **Objective:** Track the total amount received from borrowers to assess the bank's cash flow and loan repayment.
- **Metrics:**
  - **Total Amount Received**
    ```sql
    SELECT SUM(total_payment) as Total_Amount_Received FROM bank_loan_data;
    ```
  - **MTD Total Amount Received**
    ```sql
    SELECT SUM(total_payment) as MTD_Total_Amount_Received 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=12 AND YEAR(issue_date)=2021;
    ```
  - **Month-over-Month (MoM) Changes**
    ```sql
    SELECT SUM(total_payment) as PMTD_Total_Amount_Received 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=11 AND YEAR(issue_date)=2021;
    ```

### Average Interest Rate
- **Objective:** Calculate the average interest rate across all loans.
- **Metrics:**
  - **Average Interest Rate**
    ```sql
    SELECT ROUND(AVG(int_rate) * 100 ,2) AS Avg_Interest_Rate FROM bank_loan_data;
    ```
  - **MTD Average Interest Rate**
    ```sql
    SELECT ROUND(AVG(int_rate) * 100 ,2) AS MTD_Avg_Interest_Rate 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=12 AND YEAR(issue_date)=2021;
    ```
  - **Month-over-Month (MoM) Changes**
    ```sql
    SELECT ROUND(AVG(int_rate) * 100 ,2) AS PMTD_Avg_Interest_Rate 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=11 AND YEAR(issue_date)=2021;
    ```

### Average Debt-to-Income Ratio (DTI)
- **Objective:** Evaluate the average DTI for borrowers to gauge their financial health.
- **Metrics:**
  - **Average DTI**
    ```sql
    SELECT ROUND(AVG(dti) * 100, 2) AS Avg_DTI FROM bank_loan_data;
    ```
  - **MTD Average DTI**
    ```sql
    SELECT ROUND(AVG(dti) * 100, 2) AS MTD_Avg_DTI 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=12 AND YEAR(issue_date)=2021;
    ```
  - **Month-over-Month (MoM) Changes**
    ```sql
    SELECT ROUND(AVG(dti) * 100, 2) AS PMTD_Avg_DTI 
    FROM bank_loan_data
    WHERE MONTH(issue_date)=11 AND YEAR(issue_date)=2021;
    ```

### Good Loan vs. Bad Loan KPIs

- **Good Loan Metrics:**
  - **Good Loan Percentage**
    ```sql
    SELECT 
    (COUNT(CASE WHEN loan_status='Fully Paid' OR loan_status='Current' THEN id END)*100.0)/
    COUNT(id) AS Good_Loan_Percentage 
    FROM bank_loan_data;
    ```
  - **Good Loan Applications**
    ```sql
    SELECT COUNT(id) AS Good_Loan_Application 
    FROM bank_loan_data
    WHERE loan_status='Fully Paid' OR loan_status='Current';
    ```
  - **Good Loan Funded Amount**
    ```sql
    SELECT SUM(loan_amount) AS Good_Loan_Funded_Amount 
    FROM bank_loan_data
    WHERE loan_status='Fully Paid' OR loan_status='Current';
    ```
  - **Good Loan Total Received Amount**
    ```sql
    SELECT SUM(total_payment) AS Good_Loan_Received_Amount 
    FROM bank_loan_data
    WHERE loan_status='Fully Paid' OR loan_status='Current';
    ```

- **Bad Loan Metrics:**
  - **Bad Loan Percentage**
    ```sql
    SELECT
    (COUNT(CASE WHEN loan_status='Charged Off' THEN id END)*100.0)
    / COUNT(id) AS Bad_Loan_Percentage
    FROM bank_loan_data;
    ```
  - **Bad Loan Applications**
    ```sql
    SELECT COUNT(id) AS Total_Bad_Loan_Application 
    FROM bank_loan_data
    WHERE loan_status='Charged Off';
    ```
  - **Bad Loan Funded Amount**
    ```sql
    SELECT SUM(loan_amount) AS Bad_Loan_Funded_Amount 
    FROM bank_loan_data
    WHERE loan_status='Charged Off';
    ```
  - **Bad Loan Total Received Amount**
    ```sql
    SELECT SUM(total_payment) AS Bad_Loan_Received_Amount 
    FROM bank_loan_data
    WHERE loan_status='Charged Off';
    ```

### Loan Status Grid View
- **Objective:** Provide a comprehensive view of lending operations categorized by loan status.
- **Metrics:**
  - **Total Loan Applications**
  - **Total Funded Amount**
  - **Total Amount Received**
  - **Month-to-Date (MTD) Funded Amount**
  - **MTD Amount Received**
  - **Average Interest Rate**
  - **Average Debt-to-Income Ratio (DTI)**
### Loan Status Grid View
- **Objective:** Provide a comprehensive view of lending operations categorized by loan status.

  - **Loan Status Overview**
    ```sql
    SELECT 
        loan_status,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received,
        AVG(int_rate) * 100 AS Total_Int_Rate,
        AVG(dti) * 100 AS DTI
    FROM bank_loan_data
    GROUP BY loan_status;
    ```
  - **Month-to-Date (MTD)**
    ```sql
    SELECT 
        loan_status,
        SUM(loan_amount) AS MTD_Total_Funded_Amount,
        SUM(total_payment) AS MTD_Total_Amount_Received
    FROM bank_loan_data
    WHERE MONTH(issue_date) = 12
    GROUP BY loan_status;
    ```

### Monthly Trends by Issue Date
- **Objective:** Identify seasonality and long-term trends in lending activities.

  
    ```sql
    SELECT 
        MONTH(issue_date) AS Month_Number,
        DATENAME(MONTH, issue_date) AS Loan_disbursed_month,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan_data
    GROUP BY MONTH(issue_date), DATENAME(MONTH, issue_date)
    ORDER BY MONTH(issue_date);
    ```

    ### Regional Analysis by State
- **Objective:** Assess regions with significant lending activity and identify regional disparities.
  - **State-wise Loan Analysis**
    ```sql
    SELECT 
        address_state,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan_data
    GROUP BY address_state
    ORDER BY SUM(loan_amount) DESC;
    ```
### Loan Term Analysis
- **Objective:** Understand the distribution of loans across various term lengths.

  - **Total Loan Applications by Term Length**
    ```sql
    SELECT 
        term AS Term_Length,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan_data
    GROUP BY term;
    ```

### Employee Length Analysis
- **Objective:** Evaluate how lending metrics are distributed among borrowers with different employment lengths.

  - **Total Loan Applications by Employee Length**
    ```sql
    SELECT 
        emp_length,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan_data
    GROUP BY emp_length
    ORDER BY COUNT(id) DESC;
    ```

### Loan Purpose Analysis
- **Objective:** Provide a visual breakdown of loan metrics based on the stated purposes of loans to understand the primary reasons for seeking financing.

  - **Total Loan Applications by Loan Purpose**
    ```sql
    SELECT 
        purpose AS PURPOSE_OF_LOAN,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan_data
    GROUP BY purpose
    ORDER BY COUNT(id) DESC;
    ```

### Home Ownership Analysis
- **Objective:** Provide a hierarchical view of how home ownership impacts loan applications and disbursements.

  - **Total Loan Applications by Home Ownership**
    ```sql
    SELECT 
        home_ownership,
        COUNT(id) AS Total_Loan_Application,
        SUM(loan_amount) AS Total_Funded_Amount,
        SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan_data
    GROUP BY home_ownership
    ORDER BY COUNT(id) DESC;
    ```

# Steps to Implement KPIs and Visualizations

### 1. Define the Problem Statement
- Understand the key performance indicators (KPIs) required for analyzing loan data, including Total Loan Applications, Total Funded Amount, Total Amount Received, Average Interest Rate, and Average Debt-to-Income Ratio (DTI).
- Identify metrics for Good and Bad Loans.

### 2. Write SQL Queries
- **Total Loan Applications:** Write a SQL query to compute the total number of loan applications, Month-to-Date (MTD) applications, and Month-over-Month (MoM) changes.
- **Total Funded Amount:** Create a SQL query to calculate the total funded amount, MTD funded amount, and analyze MoM changes.
- **Total Amount Received:** Develop a SQL query to track the total amount received, MTD amount received, and observe MoM changes.
- **Average Interest Rate:** Formulate a SQL query to compute the average interest rate, MTD average interest rate, and MoM variations.
- **Average Debt-to-Income Ratio (DTI):** Write a SQL query to evaluate the average DTI, MTD average DTI, and MoM fluctuations.
- **Good Loan vs. Bad Loan KPIs:** Create SQL queries for metrics related to Good and Bad Loans, such as percentages, counts, funded amounts, and total received amounts.
- **Loan Status Grid View:** Develop a SQL query to provide a grid view report categorized by loan status, including metrics such as Total Loan Applications, Total Funded Amount, and Average Interest Rate.


### 3. Implement in Power BI
- **Data Import:** Import the SQL query results into Power BI.
- **Data Modeling:** Create relationships between tables if necessary, and define calculated columns or measures for KPIs.
- **Visualizations:** Develop the following charts:
  - **Monthly Trends by Issue Date (Line Chart):** Visualize seasonality and long-term trends in loan applications and funding.
  - **Regional Analysis by State (Filled Map):** Show regional disparities in lending activity and highlight regions with significant lending.
  - **Loan Term Analysis (Donut Chart):** Display the distribution of loans across various term lengths to understand loan term preferences.
  - **Employee Length Analysis (Bar Chart):** Evaluate how lending metrics are distributed among borrowers with different lengths of employment.
  - **Loan Purpose Breakdown (Bar Chart):** Provide a visual breakdown of loan metrics based on the stated purposes of loans to identify common loan purposes.
  - **Home Ownership Analysis (Tree Map):** Illustrate how home ownership impacts loan applications and disbursements, providing insights into borrower profiles.

### 4. Validate and Verify Data
- **Check Accuracy:** Ensure that the SQL queries return accurate results and that the data imported into Power BI matches expectations.
- **Cross-Verify with SQL Results:** Compare Power BI visualizations with raw SQL query results to verify correctness.
- **Adjust and Refine:** Make any necessary adjustments to queries or visualizations based on validation results.

### 5. Document the Findings
- **KPI Definitions:** Clearly document definitions and calculations for each KPI.
- **Visualization Descriptions:** Provide descriptions and insights for each chart and visualization.
- **Report Summary:** Summarize key findings and insights derived from the data and visualizations.

### 6. Share the Dashboard
- **Publish:** Publish the Power BI dashboard to the designated platform or workspace.
- **Access:** Ensure that stakeholders have access to the dashboard and understand how to interpret the visualizations.
- **Feedback:** Gather feedback from users to make any final adjustments and improve the dashboard based on their input.
  





