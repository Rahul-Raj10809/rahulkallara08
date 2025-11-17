%md
#Objective
build an end-to-end metadata-driven data engineering and analytics pipeline on Databricks using Apache Spark.
#Datasets
A. accounts.json
Bank account master data.
 Includes nested fields and time-based information.
Key fields:
•	account_id
•	customer_id
•	account_type
•	account_status
•	current_balance, available_balance
•	opening_date, last_transaction_date
•	branch_code
•	is_joint_account
•	nominee_details (nested)
•	created_timestamp

B. branches.json
Branch master details, including nested address and operational metadata.
Key fields:
•	branch_code
•	branch_name, branch_type
•	address (nested)
•	contact_details (nested, contains array)
•	operational_details (nested)
•	services_offered (array)
•	region, establishment_date, compliance_score
•	is_active, last_updated

C. customer.csv
Customer demographic and financial profile.
Key fields:
•	customer_id
•	first_name, last_name
•	email, phone
•	date_of_birth, gender
•	annual_income
•	pan_number, aadhar_number
•	city, state, pincode
•	customer_since
•	kyc_status
•	credit_score, risk_category
•	is_active

D. transaction.csv
Account-level transaction data including payments, transfers, and channel usage.
Key fields:
•	transaction_id
•	from_account_id, to_account_id
•	transaction_type
•	amount, fee_amount, currency
•	transaction_date, transaction_timestamp
•	channel (ATM, Branch, Mobile, Online)
•	merchant_name, merchant_category
•	location_city, location_state
•	device_type, ip_address
•	status (Completed / Failed)

#Architecture
Medallion architecture

#Steps Followed
Build a reusable ingestion framework that reads dataset metadata and loads files dynamically.
Cleaned, standardized, and integrated the datasets into curated Silver tables.
Generated meaningful banking KPIs from Silver tables.

#Derived KPIs
A. Customer Analytics
1.	Customer Count by Risk Category
2.	Average Annual Income per State
3.	Customer Age Distribution
4.	Top 10 Customers by Total Transaction Amount

B. Account Analytics
1.	Active vs. Dormant Accounts
2.	Average Balance by Account Type
3.	Branch-wise Total Balance Held
4.	Accounts Below Minimum Balance Threshold

C. Transaction Analytics
1.	Total Transaction Volume & Value (Monthly)
2.	Failed vs Completed Transaction Ratio
3.	Most Frequently Used Transaction Channels
4.	Merchant Category Contribution to Revenue
5.	Geographical Transaction Heatmap (State-wise)

D. Risk & Fraud Indicators (Basic)
1.	High-value Transactions (> configurable threshold)
2.	High-risk customers making failed transactions
3.	Dormant accounts with recent activity
4.	Multiple failed attempts from same IP
