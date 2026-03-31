# Customer Trends Data Analysis

A comprehensive data analysis project exploring customer shopping behavior patterns using SQL, Python, and data visualization tools. This project analyzes 3,900 customer records to uncover insights about purchasing trends, customer segmentation, and revenue drivers.

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [Key Analyses](#key-analyses)
- [SQL Queries](#sql-queries)
- [Python Analysis](#python-analysis)
- [Usage](#usage)
- [Key Findings](#key-findings)

## Overview

This project performs end-to-end analysis of customer shopping behavior data, including:

- Data cleaning and preprocessing
- Feature engineering
- Statistical analysis
- SQL-based business intelligence queries
- Database integration (PostgreSQL, MySQL, MS SQL Server)
- Customer segmentation and behavior patterns

## Dataset

**File**: `customer_shopping_behavior.csv`

The dataset contains 3,900 customer records with 18 features:

| Column | Description |
|--------|-------------|
| Customer ID | Unique identifier for each customer |
| Age | Customer age (18-70 years) |
| Gender | Male/Female |
| Item Purchased | Product name (25 unique items) |
| Category | Product category (Clothing, Footwear, Outerwear, Accessories) |
| Purchase Amount (USD) | Transaction amount ($20-$100) |
| Location | US state where purchase was made (50 states) |
| Size | Product size (S, M, L, XL) |
| Color | Product color (25 unique colors) |
| Season | Season of purchase (Spring, Summer, Fall, Winter) |
| Review Rating | Customer rating (2.5-5.0) |
| Subscription Status | Whether customer has subscription (Yes/No) |
| Shipping Type | Delivery method (Express, Standard, Free Shipping, etc.) |
| Discount Applied | Whether discount was used (Yes/No) |
| Promo Code Used | Whether promo code was applied (Yes/No) |
| Previous Purchases | Number of past purchases |
| Payment Method | Payment type (Credit Card, PayPal, Venmo, etc.) |
| Frequency of Purchases | How often customer shops (Weekly, Monthly, etc.) |

## Technologies Used

- **Python 3.x**
  - pandas - Data manipulation and analysis
  - SQLAlchemy - Database connectivity
  - psycopg2 - PostgreSQL adapter
  - pymysql - MySQL adapter
  - pyodbc - MS SQL Server adapter

- **SQL Databases**
  - PostgreSQL (primary)
  - MySQL (compatible)
  - MS SQL Server (compatible)

- **Tools**
  - Jupyter Notebook
  - Power BI (for visualization)

## Project Structure

```
.
├── customer_shopping_behavior.csv           # Raw dataset
├── Customer_Shopping_Behavior_Analysis.ipynb # Python analysis notebook
├── customer_behavior_sql_queries.sql        # SQL queries for insights
├── README.md                                # Project documentation
└── LICENSE                                  # License file
```

## Setup Instructions

### Prerequisites

- Python 3.7 or higher
- PostgreSQL, MySQL, or MS SQL Server installed
- Jupyter Notebook
- Power BI Desktop (optional, for visualization)

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd customer-trends-data-analysis-SQL-Python-PowerBI-main
```

2. Install required Python packages:
```bash
pip install pandas sqlalchemy psycopg2-binary pymysql pyodbc
```

3. Set up your database:

**For PostgreSQL:**
```sql
CREATE DATABASE customer_behavior;
```

**For MySQL:**
```sql
CREATE DATABASE customer_behavior;
```

**For MS SQL Server:**
```sql
CREATE DATABASE customer_behavior;
```

4. Update database credentials in the Jupyter notebook:
   - Username
   - Password
   - Host
   - Port
   - Database name

5. Launch Jupyter Notebook:
```bash
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

## Key Analyses

### Data Cleaning & Preprocessing

- **Missing Data Handling**: 37 missing values in Review Rating column imputed using median rating per category
- **Column Standardization**: Renamed columns to snake_case for consistency
- **Feature Engineering**:
  - Created `age_group` column (Young Adult, Adult, Middle-aged, Senior)
  - Created `purchase_frequency_days` column (converted frequency text to numeric days)
  - Dropped redundant `promo_code_used` column (identical to `discount_applied`)

### Customer Segmentation

Customers segmented into three tiers based on purchase history:
- **New**: 1 previous purchase
- **Returning**: 2-10 previous purchases
- **Loyal**: 11+ previous purchases

## SQL Queries

The project includes 10 comprehensive SQL queries analyzing:

1. **Revenue by Gender** - Total revenue comparison between male and female customers
2. **Discount Optimization** - Customers using discounts but spending above average
3. **Top Rated Products** - Top 5 products by average review rating
4. **Shipping Analysis** - Purchase amount comparison by shipping type
5. **Subscription Impact** - Revenue and spending patterns of subscribers vs. non-subscribers
6. **Discount Patterns** - Products with highest discount usage percentage
7. **Customer Segmentation** - Distribution of New, Returning, and Loyal customers
8. **Category Insights** - Top 3 products within each category
9. **Repeat Buyer Behavior** - Subscription likelihood for repeat buyers (5+ purchases)
10. **Age Group Revenue** - Revenue contribution by age demographic

## Python Analysis

The Jupyter notebook (`Customer_Shopping_Behavior_Analysis.ipynb`) includes:

### Data Exploration
- Dataset loading and initial inspection
- Statistical summary analysis
- Data type validation

### Data Preprocessing
- Missing value detection and imputation
- Column renaming and standardization
- Duplicate column removal

### Feature Engineering
- Age group categorization using quartiles
- Purchase frequency conversion to numeric days
- Data type optimization

### Database Integration
- PostgreSQL connection setup
- MySQL connection (alternative)
- MS SQL Server connection (alternative)
- Automated table creation and data loading

## Usage

### Running SQL Queries

1. Load data into your database using the Jupyter notebook
2. Open `customer_behavior_sql_queries.sql` in your SQL client
3. Execute queries individually or as needed

### Running Python Analysis

1. Open the Jupyter notebook:
```bash
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

2. Update database credentials in the connection cell
3. Run all cells sequentially

### Database Connection Examples

**PostgreSQL:**
```python
engine = create_engine(f"postgresql+psycopg2://{username}:{password}@{host}:{port}/{database}")
```

**MySQL:**
```python
engine = create_engine(f"mysql+pymysql://{username}:{password}@{host}:{port}/{database}")
```

**MS SQL Server:**
```python
driver = quote_plus("ODBC Driver 17 for SQL Server")
engine = create_engine(f"mssql+pyodbc://{username}:{password}@{host},{port}/{database}?driver={driver}")
```

## Key Findings

Based on the analysis structure, this project helps answer:

- Which gender drives more revenue?
- Do subscribers spend more than non-subscribers?
- What products receive the highest ratings?
- How do shipping preferences affect purchase amounts?
- Which products benefit most from discounts?
- What is the distribution of customer loyalty levels?
- Are repeat buyers more likely to subscribe?
- Which age groups contribute most to revenue?
- What are the bestselling products in each category?

## Database Schema

After loading the data, the `customer` table includes:

- customer_id (INTEGER)
- age (INTEGER)
- gender (VARCHAR)
- item_purchased (VARCHAR)
- category (VARCHAR)
- purchase_amount (INTEGER)
- location (VARCHAR)
- size (VARCHAR)
- color (VARCHAR)
- season (VARCHAR)
- review_rating (FLOAT)
- subscription_status (VARCHAR)
- shipping_type (VARCHAR)
- discount_applied (VARCHAR)
- previous_purchases (INTEGER)
- payment_method (VARCHAR)
- frequency_of_purchases (VARCHAR)
- age_group (VARCHAR)
- purchase_frequency_days (INTEGER)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the terms specified in the LICENSE file.

## Contact

For questions or feedback, please open an issue in the repository.

---

**Note**: This is an educational/portfolio project demonstrating data analysis skills using SQL, Python, and business intelligence tools.
