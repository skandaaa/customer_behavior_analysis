#Customer Shopping Behavior Analysis
A end-to-end data analysis project covering data ingestion, exploratory data analysis, data cleaning, SQL-based business analysis in PostgreSQL, and an interactive Power BI dashboard — all built around a retail customer shopping dataset.

#Overview
This project analyzes the shopping behavior of 3,900 retail customers to uncover patterns in spending, product preferences, discount usage, and subscription behavior. The goal is to turn raw transactional data into actionable business insights through structured analysis and visual storytelling.

#Dataset
DetailInfoFilecustomer_shopping_behavior.csvRecords3,900 rowsFeatures18 columnsSourceRetail customer transaction data
Key columns: Customer ID, Age, Gender, Item Purchased, Category, Purchase Amount (USD), Location, Season, Review Rating, Subscription Status, Shipping Type, Discount Applied, Previous Purchases, Payment Method, Frequency of Purchases

#Tools & Technologies
LayerToolLanguagePython 3.12EnvironmentAnaconda / Jupyter NotebookData ManipulationPandasDatabasePostgreSQLDB ConnectorSQLAlchemy, psycopg2VisualizationPower BI

#Project Steps
1. Data Loading

Loaded the CSV dataset into a Pandas DataFrame
Connected to a local PostgreSQL database (customer_behavior) using SQLAlchemy
Pushed the cleaned DataFrame into a PostgreSQL table named customer

2. Exploratory Data Analysis (EDA)

Inspected dataset shape, data types, and summary statistics using df.info() and df.describe()
Identified missing values — Review Rating had nulls, filled using category-wise median imputation
Explored distributions across age, gender, season, and purchase amount

3. Data Cleaning & Feature Engineering

Standardized all column names to snake_case for SQL compatibility
Renamed purchase_amount_(usd) → purchase_amount
Engineered an age_group feature using pd.qcut() — segmented into: Young Adult, Adult, Middle-aged, Senior
Mapped frequency_of_purchases (text) to numeric purchase_frequency_days
Dropped the promo_code_used column after confirming it was fully redundant with discount_applied

4. SQL Analysis (PostgreSQL)
Ran 10 business-focused SQL queries on the customer table:
QueryQ1Total revenue by genderQ2Discount users who spent above averageQ3Top 5 products by average review ratingQ4Average spend — Standard vs. Express shippingQ5Subscriber vs. non-subscriber revenue comparisonQ6Top 5 products with highest discount rateQ7Customer segmentation — New, Returning, LoyalQ8Top 3 products per category (window function)Q9Repeat buyers vs. subscription statusQ10Revenue contribution by age group
5. Power BI Dashboard
Built an interactive dashboard visualizing key business metrics with slicers for Gender, Season, and Subscription Status.

#Dashboard
File: Customer Shopping Behavior.pbix
Visuals included:

#Revenue breakdown by gender and age group
Top-selling product categories by season
Subscription vs. non-subscription spend comparison
Discount impact on purchase behavior
Customer loyalty segmentation chart
Shipping type vs. average order value


Open the .pbix file in Power BI Desktop to explore the interactive dashboard.


#Key Results

Subscribed customers generate significantly higher total revenue despite similar average spend per transaction
Loyal customers (10+ previous purchases) make up a disproportionate share of revenue
Certain product categories show discount rates above 60%, pointing to potential margin risk
Middle-aged and Senior customers contribute the most revenue by age group
Products like Blouse and Jewelry consistently rank highest in customer review ratings


#How to Run
Prerequisites

Python 3.12 with Anaconda
PostgreSQL installed and running locally
Power BI Desktop (for dashboard)

#Steps
1. Clone or download the project
bashgit clone <your-repo-url>
cd customer-shopping-behavior
2. Install dependencies
bashpip install pandas sqlalchemy psycopg2-binary
3. Set up PostgreSQL

Create a database named customer_behavior in PostgreSQL
Update the credentials in the notebook if needed:

pythonusername = "your_username"
password = "your_password"
host = "localhost"
port = "5432"
database = "customer_behavior"
4. Run the Jupyter Notebook
bashjupyter notebook customer_shopping_behavior.ipynb
Run all cells top to bottom — this performs EDA, cleans the data, and loads it into PostgreSQL.
5. Run SQL Queries

Open customer_behavior_sql_queries.sql in pgAdmin or any PostgreSQL client
Execute queries against the customer_behavior database

6. Open the Dashboard

Open Customer Shopping Behavior.pbix in Power BI Desktop


#Project Structure
Customer Shopping Behavior/
├── customer_shopping_behavior.csv       # Raw dataset
├── customer_shopping_behavior.ipynb     # EDA, cleaning & DB load (Python)
├── customer_behavior_sql_queries.sql    # 10 business SQL queries (PostgreSQL)
└── Customer Shopping Behavior.pbix     # Power BI dashboard

Built by Skanda | ML Engineer & Data A
