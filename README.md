README: CaseTechAE_XP202412
This README describes the technical implementation and considerations of the CaseTechAE_XP202412 notebook, which explores customer portfolio alignment within XP's B2B investment platform. The notebook utilizes Databricks with PySpark and SQL to process and analyze datasets related to investment strategies, customer suitability profiles, and portfolio optimization.

Purpose
The primary objective is to enhance customer portfolio adherence to recommended investment strategies based on suitability, aiming to increase portfolio safety, returns, and XP’s revenue. This is achieved through data transformations, aggregations, and analyses to identify discrepancies and suggest improvements.

Project Structure
The project is structured into multiple challenges:

1. Data Preparation
Transform raw CSV files into structured Databricks tables.
Data tables include:
FAT_ (Fact tables): Store historical transactional data, potentially repeated over time.
DIM_ (Dimension tables): Provide contextual metadata for fact tables (e.g., customer profiles, products).
2. Data Transformation
Create fat_custodia_conta_mensal, a fact table summarizing monthly custody at the customer level:
Columns:
COD_DIM_TEMPO
COD_DIM_CONTA
CANAL
SUITABILITY
CLASSE_N1 (Product Strategy)
VAL_POSICAO (Custody Value)
3. Challenge 1: Portfolio Allocation
Aggregate customer portfolios to:

Identify the most recent custody for each customer and strategy.
Compute allocation percentages for each product strategy in the portfolio.
Output Columns:

COD_DIM_CONTA
SUITABILITY
ESTRATEGIA (Strategy)
CUSTODIA (Custody Value)
ALOCACAO (Percentage Allocation)
4. Challenge 2: Allocation Discrepancies
Compare actual portfolio allocations to recommended allocations (fat_recomendacao).

Identify discrepancies and calculate absolute differences in allocation percentages.

Highlight the top 5 customers with the highest total allocation discrepancies.

Output Columns:

COD_DIM_CONTA
SUITABILITY
ESTRATEGIA
CUSTODIA
ALOCACAO (Actual)
ALOCACAO_RECOMENDADA
DESVIO_ALOCACAO (Absolute Difference)
5. Challenge 3: Strategic Recommendations
Utilize the provided TB_ROA_MEDIO table to calculate potential revenue impact if customers reallocate their portfolios to match recommendations.
Additional analyses include:
Revenue potential under recommended allocation.
Historical trends in product distribution for customers with high discrepancies.
Portfolio distributions in B2B vs. B2C channels.
Key Functions and Queries
Python Functions
read_csv: Reads and parses CSV files into Spark DataFrames with specified schema.
Transformations:
Use PySpark’s join, groupBy, agg, and window functions to manipulate and analyze large datasets efficiently.
SQL Queries
Enable SQL-based analysis through temporary views, allowing a hybrid approach of SQL and PySpark.
Technical Considerations
Data Volume and Optimization
Employ Spark optimizations like partitioning, caching, and schema inference to handle large datasets efficiently.
Dynamic Suitability
Adjust for monthly changes in suitability and recommendations by filtering on the most recent data.
Suggested Improvements
Revenue Projections
Predict future revenue based on ROA adjustments for portfolio realignment.
Portfolio Insights
Analyze trends in customer allocation and suitability over time.
Visualize discrepancies and strategies using Databricks notebooks.
This notebook demonstrates a data-driven approach to align customer portfolios with recommended strategies, ensuring compliance with suitability profiles while enhancing XP's financial performance.
