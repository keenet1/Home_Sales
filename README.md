# Home_Sales

Contributor: Thomas Keene
---

![House for Sale](https://github.com/keenet1/Home_Sales/assets/137319054/e2693f96-6b79-4eb5-a8b3-539c74d47515)

## Introduction   
In this repository, I demonstrate how SparkSQL can be used to determine key metrics about home sales data. Spark is utilized to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached.   
  
## Findings   
**What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.**

![image for 5_1](https://github.com/keenet1/Home_Sales/assets/137319054/ae24e9c9-6e4d-4dcf-8417-1cb2d2b890d3)

From the table above, it can be seen that the average price for a four-bedroom house (for the years shown) is approximately $299,200.20 with minor year-to-year fluctuations.

**What is the average price of a home for each year it was built that has three bedrooms and three bathrooms? Round off your answer to two decimal places.**

![Image for 5_2](https://github.com/keenet1/Home_Sales/assets/137319054/ab613106-a521-4f7b-af65-9c4fb05fdd51)

From the table above, it can be seen that the average price for a three-bedroom, three-bathroom house (for the years shown) is approximately $292,059.62. While prices fluctuate year-to-year, no homes are valued at or above $300,000.00 for the years shown.

**What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.**

![Image for 5_3](https://github.com/keenet1/Home_Sales/assets/137319054/7c498e1e-3b02-4fee-8077-c5e00baea7b7)

From the table above, it can be seen that the average price for a two-floor home with 2,000 or more square feet with three bedrooms and three bathrooms (for the years shown) is approximately $292,867.27. Over the time period shown, the average price ranged from a minimum of 276553.81 in 2011 to a maximum of 307539.97 in 2012.   

## Query Time Comparisons
Three SparkSQL queries were executed using the same question to determine the run times for:
- A query performed on the original data set
- A query performed on a cached copy of the original data set
- A query performed on the original data set after parquet formatting was applied and the data were partitioned on date_built

The question used for the comparison was: "What is the "view" rating for homes costing more than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places."   

**Query performed on the original data set**   
![Original Data Query](https://github.com/keenet1/Home_Sales/assets/137319054/35d96116-acc7-41cb-a1b3-306215388f93)   

**Query performed on a cached copy of the original data set**   
![Cached Data Query](https://github.com/keenet1/Home_Sales/assets/137319054/2e405655-ced5-4d26-b910-0c3b47461eb8)   

**Query performed on the original data set after parquet formatting was applied and the data were partitioned on date_built**   
![Parquet Data Query](https://github.com/keenet1/Home_Sales/assets/137319054/8d90ec53-e982-4214-88e7-c84b9a9fd90d)   

As can be seen from the run times displayed under each table, the parquet runtime of 0.771 seconds was slightly longer than the cached runtime of 0.597 seconds but shorter than the original-uncached runtime of 1.059 seconds.

## Summary and Conclusion:
Overall, the query run times were shorter for the queries that were executed on the cached data as well as on the parquet formatted data (as compared to the query run time that was performed on the original data set). Generally, caching the data allows the query faster access to the data (as the data is stored in memory) and as such, the overall query process can be executed more quickly. On the other hand, Parquet formatting of the data (along with partitioning) essentially allows the query to be performed on only the most relevant data, which also allows for the query to be executed more quickly as well.

Resources:  
Web Resources:
https://spark.apache.org/docs/latest/api/python/index.html#:~:text=PySpark%20is%20the%20Python%20API,for%20interactively%20analyzing%20your%20data.   
https://arrow.apache.org/docs/python/parquet.html   
https://fastparquet.readthedocs.io/en/latest/   

Some coding I looked at for inspiration:  
https://github.com/Hamim-Hussain/Home_Sales   

Acknowledgements:  
I wish to thank my teaching staff:  
Hunter Hollis  
Sam Espe  
Randy Sendek

