## Project: Analyze International Debt Statistics (SQL Beginner)

Humans not only take debts to manage necessities. A country may also take debt to manage its economy. For example, infrastructure spending is one costly ingredient required for a country's citizens to lead comfortable lives. The World Bank is the organization that provides debt to countries.

In this project, you are going to analyze international debt data collected by The World Bank. The dataset contains information about the amount of debt (in USD) owed by developing countries across several categories. You are going to find the answers to the following questions:

- What is the number of distinct countries present in the database?
- What country has the highest amount of debt?
- What country has the lowest amount of repayments?

Below is a description of the table you will be working with:

## `international_debt` table

| Column | Definition | Data Type |
| --- | --- | --- |
| country_name | Name of the country | `varchar` |
| country_code | Code representing the country | `varchar` |
| indicator_name | Description of the debt indicator | `varchar` |
| indicator_code | Code representing the debt indicator | `varchar` |
| debt | Value of the debt indicator for the given country (in current US dollars) | `float` |

You will execute SQL queries to answer three questions, as listed in the instructions.


### Quick look at the table
```sql
SELECT *
FROM international_debt;
```
![image](https://github.com/NguyenMav/DataCamp_SQL_Beginner_International_Debt/assets/149219810/b0c59170-cb8a-4130-9d5d-dd524aeb5a02)


### What is the number of distinct countries present in the database?
```sql
-- num_distinct_countries 
SELECT COUNT(DISTINCT country_name) AS total_distinct_countries
FROM international_debt;
```
![image](https://github.com/NguyenMav/DataCamp_SQL_Beginner_International_Debt/assets/149219810/bd8a7e00-12bd-49cb-a2b3-e7fba011455a)


### What country has the highest amount of debt?
```sql
-- highest_debt_country 
SELECT country_name, SUM(debt) AS total_debt
FROM international_debt
GROUP BY country_name
ORDER BY total_debt DESC
LIMIT 1;
```
![image](https://github.com/NguyenMav/DataCamp_SQL_Beginner_International_Debt/assets/149219810/da199bcf-73bb-4904-806b-66b99895546f)


### What country has the lowest amount of repayments?
```sql
-- lowest_principal_repayment 
SELECT country_name, indicator_name, debt AS lowest_repayment
FROM international_debt
WHERE indicator_code = 'DT.AMT.DLXF.CD'
ORDER BY lowest_repayment ASC
LIMIT 1;
```
![image](https://github.com/NguyenMav/DataCamp_SQL_Beginner_International_Debt/assets/149219810/b01349e5-a307-4388-9816-667001cbfefe)
