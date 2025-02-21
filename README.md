# fetch-assignment
# Exercise:
## First: explore the data
Review the unstructured csv files and answer the following questions with code that supports your conclusions: 

**Are there any data quality issues present?** 
- Missing data in all tables. Transaction table had different types of missing data, such as empty cell and Nan, so those had to be accounted for. The Products table contains 8,122 unique brands, but approximately 27% of the Manufacturer Name and Brand Name fields are missing.
- Some `BIRTH_DATE` are on or shortly after `CREATE_DATE` in the `users` table. Could this be due to users not inputting birth_dates? It's unlikely that young children (and most certainly not 2 year olds) are making purchases and receiving rewards.

**Are there any fields that are challenging to understand?**
- Bit confusing why FINAL_QUANTITY in Transactions could be 0, but the cost was greater than $0.
- Dates were formatted with DATETIME, I believe in Zulu time or UTC (with the Z following each date). To avoid confusion I preprocessed these to just have the month, day, and year.
 

## Second: provide SQL queries
Answer three of the following questions with at least one question coming from the closed-ended and one from the open-ended question set. *Each question should be answered using one query.*

#### Closed-ended questions:
**What are the top 5 brands by receipts scanned among users 21 and over?** 
> ### Answer: Nerds Candy, Dove, Sour Patch Kids, Hershey's, Coca-Cola

**What are the top 5 brands by sales among users that have had their account for at least six months?**\
> ### Answer: Coca-cola, Annie's Homegrown Grocery, Dove, Barefoot, Oribe.


#### Open-ended questions: make assumptions and clearly state them.
**Which is the leading brand in the Dips & Salsa category?** 
> #### Assumptions: I will rank the leading brand by SALES. Though there are only 89 days worth of Purchases in the Transactions table, so this is just leading brand for the quarter (Approximately June to September of 2024)
> ### Answer: It's Tostitos, with a total sales of $103,354.84



## Third: communicate with stakeholders
**Construct an email or slack message that is understandable to a product or business leader who is not familiar with your day-to-day work. Summarize the results of your investigation.** 

Include:
* Key data quality issues and outstanding questions about the data 
* One interesting trend in the data 
  * Use a finding from part 2 or come up with a new insight 
* Request for action: explain what additional help, info, etc. you need to make sense of the data and resolve any outstanding issues

## **Email:**

**Subject:** Data Quality Review & Key Insights 

Hi [Team Leader],

I’ve wanted to share some key findings after reviewing the data on user transactions and products:

**Data Quality Observations:**

* Missing data is present across all tables, including user birthdates, transaction details, and products' manufacturer names and brand names.
* Some `BIRTH_DATE` values are on or just after `CREATE_DATE`, which may indicate missing user input rather than actual birthdates.
* In the Transactions table, `FINAL_QUANTITY` sometimes shows as 0 despite a nonzero cost.

**Interesting Trend and Additonal Insight:**

* Among users who have been active for at least six months, the top-selling brands are **Coca-Cola, Annie’s Homegrown, Dove, Barefoot, and Oribe**, indicating a mix of beverages, grocery, and personal care brands driving engagement.
* In the Dips & Salsa category, **Tostitos leads sales for the most recent quarter, generating $103,354.84 in transactions.** Given that our dataset covers approximately 89 days, this suggests strong quarterly performance.

**Next Steps:**
1. Confirm if missing `BIRTH_DATE` values are expected, or if there’s a process gap.
2. Clarify why transactions might show `FINAL_QUANTITY` = 0 with a cost.
3. Determine whether the 89-day Transactions dataset is representative of broader trends or if we should supplement it with additional data.

Thanks,

Emily
