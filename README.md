## Project: Analyze International Debt Statistics (SQL Beginner)

Link to workbook: https://www.datacamp.com/datalab/w/7251f55e-1fd3-4098-97a8-7595e768b178/edit

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

| total_distinct_countries |
|--------------------------|
| 124                      |

### What country has the highest amount of debt?
```sql
-- highest_debt_country 
SELECT country_name, SUM(debt) AS total_debt
FROM international_debt
GROUP BY country_name
ORDER BY total_debt DESC
LIMIT 1;
```

| country_name | total_debt   |
|--------------|--------------|
| China        | 2.85793E+11  |

### What country has the lowest amount of repayments?
```sql
-- lowest_principal_repayment 
SELECT country_name, indicator_name, debt AS lowest_repayment
FROM international_debt
WHERE indicator_code = 'DT.AMT.DLXF.CD'
ORDER BY lowest_repayment ASC
LIMIT 1;
```
| country_name | indicator_name                                                      | lowest_repayment |
|--------------|----------------------------------------------------------------------|------------------|
| Timor-Leste  | Principal repayments on external debt, long-term (AMT, current US$) | 825,000          |

