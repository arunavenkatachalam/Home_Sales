# Home Sales

## Introduction

In this data, We use SparkSQL to determine key metrics about home sales data. Then we'll use Spark to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached.

## Process

1. Import the necessary PySpark SQL functions.

2. Read the home_sales csv file into a Spark DataFrame.

3. Create a temporary table called home_sales.

4. Perform some basic analysis and answered the questions in the next section.

5. Cache your temporary table home_sales.

6. Check if the temporary table is cached.

7. Using the cached data, run the query that filters out the view ratings with an average price of greater than or equal to $350,000. Determine the runtime and compare it to uncached runtime.

8. Partition by the "date_built" field on the formatted parquet home sales data.

9. Create a temporary table for the parquet data.

10. Run the query that filters out the view ratings with an average price of greater than or equal to $350,000. Determine the runtime and compare it to uncached runtime.

11. Uncache the home_sales temporary table.

12. Verify that the home_sales temporary table is uncached using PySpark.

## Questions to be answered

1. What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.

                          +-------------+----------+
                          |average_price|date_built|
                          +-------------+----------+
                          |    296576.69|      2017|
                          |    296050.24|      2016|
                          |    307908.86|      2015|
                          |    299073.89|      2014|
                          |    299999.39|      2013|
                          |    298233.42|      2012|
                          |     302141.9|      2011|
                          |    296800.75|      2010|
                          +-------------+----------+

2. What is the average price of a home for each year it was built that has three bedrooms and three bathrooms? Round off your answer to two decimal places.

                         +-------------+----------+
                         |average_price|date_built|
                         +-------------+----------+
                         |    292676.79|      2017|
                         |    290555.07|      2016|
                         |     288770.3|      2015|
                         |    290852.27|      2014|
                         |    295962.27|      2013|
                         |    293683.19|      2012|
                         |    291117.47|      2011|
                         |    292859.62|      2010|
                         +-------------+----------+

3. What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.

                       +-------------+----------+
                       |average_price|date_built|
                       +-------------+----------+
                       |    282026.59|      2017|  
                       |     287812.6|      2016|
                       |    291788.36|      2015|
                       |    294195.13|      2014|
                       |    295142.13|      2013|
                       |    295858.68|      2012|
                       |    281413.45|      2011|
                       |    280447.23|      2010|
                       +-------------+----------+

5. What is the "view" rating for homes costing more than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.

                      +----+-------------+----------+
                      |view|average_price|date_built|
                      +----+-------------+----------+
                      |  80|    1121072.2|      2017|
                      |  60|    823721.83|      2017|
                      |   1|    392578.58|      2017|
                      |  37|    396466.19|      2017|
                      |  84|     968260.5|      2017|
                      |  58|     660556.0|      2017|
                      |  29|     402341.0|      2017|
                      |  57|     732720.0|      2017|
                      |  45|     404400.3|      2017|
                      |  27|    398848.38|      2017|
                      |  74|     750350.0|      2017|
                      |   4|     397640.1|      2017|
                      |  42|    396225.38|      2017|
                      |  30|     394784.0|      2017|
                      |  35|    403808.04|      2017|
                      |  65|     665755.0|      2017|
                      |  12|    409095.89|      2017|
                      |   7|    405994.28|      2017|
                      |  33|    394572.64|      2017|
                      |  97|   1401221.67|      2017|
                      +----+-------------+----------+
                        only showing top 20 rows

                    --- 0.5897006988525391 seconds ---

## Conclusion
 
 A query is written that returns the view rating for the average price for homes that are greater than or equal to $350,000, rounded to two decimal places. the run time of this query is 1.12 minutes. Cached the home sales table and ran the same query, the run time is 0.85 seconds. comparing it is clear that after cached the table run time has decreased.Next step is to uncached the table.

 A partition of the home sales dataset by the "date_built" field is created, and the formatted parquet data is read. The same query above is run in the parquet data and the runtime is 1.53 minutes which is higher than cached query and the intial query. We might see bigger difference when we perform this on larger datasets.

 
