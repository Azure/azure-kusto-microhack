# Azure Data Explorer Microhack (Preview)

Kusto Product Group and Microsoft Global Black Belt team are pleased to present this challenge based, collaboration driven, discover-by-doing learning experience to you. Microhacks are divided into two parts to cater enough time for the participants to understand the key concepts of Azure Data Explorer effectively.

- [**Microhack 1: Cluster creation and data ingestion**](https://github.com/Azure/azure-kusto-microhack1)
This MicroHack will focus on enabling the participants to design ADX based big data analytics solution, create an ADX cluster, and ingest data into the cluster.

- [**Microhack 2: Data exploration and visualization using Kusto Query Language (KQL)**](https://github.com/Azure/azure-kusto-microhack#microhack-2-data-exploration-and-visualisation-with-kql-preview)
This MicroHack will focus on enabling the participants to write kusto queries to explore and analyse the data stored in the clusters. Participants will also create cool visualizations. It is recommended to complete the Microhack 1 before beginning with Microhack 2.

- **Microhack 3: Advanced capabilities**
This Microhack will focus on enabling the participants to create Materialized Views, Functions, and use advanced operators to explore and analyse the data.




## Microhack 2: Data exploration and visualisation with KQL (Preview)

This Microhack is organised into the following 3 challenges:
- Challenge 5: Starting with basics of KQL
- Challenge 6: Advanced KQL operators
- Challenge 7: Visualisation

Each challenge has a set of tasks that need to be completed in order to move on to the next challenge. It is advisable to complete the challenges and tasks in the prescribed order.

### Challenge 5: Starting with basics of KQL

In this challenge you’ll write queries in Kusto Query Language (KQL) to explore and gain insights from your data. 

Expected Learning Outcomes:
- Know how to write queries with KQL.
- Use KQL to explore data by using the most common operators.

**What is a Kusto query?**
A Kusto query is a read-only request to process data and return results. The request is stated in plain text that's easy to read, author, and automate. A Kusto query has one or more query statements and returns data in a tabular or graph format.

**What is a tabular statement?**
The most common kind of query statement is a tabular expression statement. Both its input and its output consist of tables or tabular datasets.

Tabular statements contain zero or more operators. Each operator starts with a tabular input and returns a tabular output. Operators are sequenced by a pipe (|). Data flows, or is piped, from one operator to the next. The data is filtered or manipulated at each step and then fed into the following step.

It's like a funnel, where you start out with an entire data table. Each time the data passes through another operator, it's filtered, rearranged, or summarized. Because the piping of information from one operator to another is sequential, the query's operator order is important. At the end of the funnel, you're left with a refined output.
Let's look at an example query:

```
LogisticsTelemetryExtended
| where enqueuedTime > ago(7d) 
| where messageSource == "telemetry"
| count 
```

This query has a single tabular expression statement. The statement begins with a reference to the table LogisticsTelemetry and contains the operators where and count. Each operator is separated by a pipe. The data rows for the source table are filtered by the value of the enqueuedTime column and then filtered by the value of the messageSource column. In the last line, the query returns a table with a single column and a single row that contains the count of the remaining rows.

References:
- [SQL to Kusto cheat sheet](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/sqlcheatsheet)
- [KQL cheat sheets](https://github.com/marcusbakker/KQL/blob/master/kql_cheat_sheet.pdf)

#### Task 0: Connect to the cluster

For the next tasks, connect to the cluster [ADX Microhack Cluster](https://adxmicrohackcluster.eastus.kusto.windows.net/)

![Screen capture 1](/assets/images/Challenge5-Task0-Pic1.png)

![Screen capture 1](/assets/images/Challenge5-Task0-Pic2.png)

We will use the table LogisticsTelemetryExtended. This table is based on  LogisticsTelemetry (we used an update policy to break the telemetry JSON column into independent columns. The update policy script can be found here <link>)

#### Task 1: Explore the table and columns
Write a query to learn the table, its columns, data types using any random 10 rows

#### Task 2: Keep the columns of your interest
Write a query to see only the desired columns

[project-away operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/projectawayoperator)
[Project operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/projectoperator)

#### Task 3: Filter the output
Write a query to see only the desired rows. Take arbitrary 10 records from the last 10 minutes.

Hint 1: “ago”
Hind 2: In case you see 0 records, remember that operators are sequenced by a pipe (|). Data is piped, from one operator to the next. The data is filtered or manipulated at each step and then fed into the following step. By using the ‘Take’ operator, there is no guarantee which records are returned

[where operator in Kusto query language - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/whereoperator)

#### Task 4: Sorting the results
Write a query to get the 5 records which have the highest temperature, from the last 3 days. Write another query get the 5 records which have the lowest temperature, from the last 20 minutes.

[sort operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/sortoperator)

#### Task 5: Reorder, rename, add columns
Write a query to convert Fahrenheit temperatures to Celsius temperatures. For readability, show them as the 2 left-most columns. You can use the following formula: 
C = (F – 32) * 5/9 <br>
Take 5 random records from the past week.
Hint 1: 'project' operator provides lot more features

[https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/extendoperator](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/extendoperator)

#### Task 6: Total number of records
Write a query to find out how many records are in the table. 

[count operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/countoperator)

#### Task 7: Aggregations and string operations
Write a query to find out how many records were created in the last 10 mins. 
Write another query to find all deviceIds starting with 'x'. 
Write another query to find out how many records start with "x" , per device ID (aggregated by device ID).

[String operators - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/datatypes-string-operators)
[summarize operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/summarizeoperator)

#### Task 8: Render a chart
Write a query to find out how many records startswith "x" , per device ID (aggregated by device ID) and render a piechart.

[render operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/renderoperator?pivots=azuredataexplorer)

#### Task 9: Create bins and visualize time series 
Write a query to show a timechart of the number of records over time. Use 1 day bins (buckets). Each point on the timechart represent the number of devices on that day.

[bin() - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/binfunction)

#### Task 10: Aggregations with time series visualisations
Write a query to show a timechart of the **average temperature** over time. Use 30 minute bins (buckets) Each point on the timechart represent the average temperature in that 30 min period.

### Challenge 6: Going more advanced with KQL

#### Task 1: Declaring variables
Write a query to create a table of the 10 device Ids which have the highest Shock, from the last 1 day. Then, use this list in a following query to find the average temperature of these 10 devices, over the last 30 days.

You can use the **'let'** statement to set a variable name equal to an expression or a function, or to create views (a virtual tables based on the result-set of another query. Just like a real table, a view contains rows and columns. ).
let statements are useful for:
- Breaking up a complex expression into multiple parts, each represented by a variable.
- Defining constants outside of the query body for readability.
- Defining a variable once and using it multiple times within a query.

Hint 1: [in operator - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/in-cs-operator#subquery)
Hint 2: [let - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/letstatement#examples)

#### Task 2: Add more fields to your timechart
Write a query to show a timechart of the number of records from the last 1 hour, by TransportationMode. Use 1 minute bins.

Expected result:

![Screen capture 1](/assets/images/Challenge6-Task2-Pic1.png)

#### Task 3: Some geo-mapping
Write a query to show on map the locations (based on the longitude and latitude) of 10 devices with the highest temperature from the last 7 days.
<br>
Hint 1: 'top' operator
Hint 2: render scatterchart with (kind = map)

Once the map is displayed, you can click on the locations. Note that in order to show more details in the balloon, you need to change the render phrase to include 'series=<TempColumn>'.

[render operator with scatter chart](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/renderoperator?pivots=azuredataexplorer)

#### Task 4: Range
Range is a tabular operator: it generates a single-column table of values, whose values are start, start + step, ... up to and until stop.
Run the following query and review the results:

range MyNumbers from 1 to 8 step 2

Range also works with dates:
range LastWeek from ago(7d) to now() step 1d

We will use the range operator as part of the time series creation in the next tasks.
  
#### Machine learning with Kusto and time series analysis

Many interesting use cases use machine learning algorithms and derive interesting insights from telemetry data. Often, these algorithms require a strictly structured dataset as their input. The raw log data usually doesn't match the required structure and size. We will see how we can use the make-series operator to create well curated data (time series).

Then, we can use built in functions like [series_decompose_anomalies](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/series-decompose-anomaliesfunction). Anomalies/ outliers will be detected by the Kusto service and highlighted as red dots on the time series chart.

**Time series:**
What is a time series?
A time series is a collection of observations of well-defined data items obtained through repeated measurements over time and listed in time order. Most commonly, the data points are consistently measured at equally spaced intervals. For example, measuring the temperature of the room each minute of the day would comprise a time series. Data collected irregularly is not a time series.

**What is time series analysis?**

Time series analysis comprises methods for analyzing time series data in order to extract meaningful statistics and other characteristics of the data. Time series forecasting, for example, is the use of a model to predict future values based on previously observed values. 

**What is time series decomposition?**
Time series decomposition involves thinking of a series as a combination of 4 components: 
- trends (increasing or decreasing value in the series)
- seasonality (repeating short-term cycle in the series)
- baseline (the predicted value of the series, which is the sum of seasonal and trend components) 
- noise (The residual random variation in the series). 
We can use built in functions, that uses time series decomposition to forecast future metric values and/or detect anomalous values.

This is how time series looks like:

![Screen capture 1](/assets/images/Challenge6-Task4-Pic1.png)

**Why should you use series instead of the summarize operator?**

The summarize operator does not add "null bins" — rows for time bin values for which there's no corresponding row in the table. It's a good idea to "pad" the table with those bins. Advanced built in ML capabilities like anomaly detection need the data points to be consistently measured at equally spaced intervals. The **make-series** can create such a “complete” series.

#### Task 4: Anomaly detection
Write a query to create an anomaly chart of the average shock, in the last 3 days.

For this task, we will provide more instructions:

To generate these series, start with:
```
let min_t = ago(3d);
let max_t = (toscalar(LogisticsTelemetryExtended | summarize max(enqueuedTime)));
let step_interval = 10m;
LogisticsTelemetryExtended
| make-series avg_shock_series=avg(Shock) on (enqueuedTime) from (min_t) to (max_t) step step_interval 
```
Now, we will use this avg_shock_series and run series_decompose_anomalies.
This built-in function takes an expression containing a series (dynamic numerical array) as input, and extracts anomalous points with scores.
```
| extend anomalies_flags = series_decompose_anomalies(avg_shock_series, 1) 
| render anomalychart  with(anomalycolumns=anomalies_flags, title='avg shock anomalies') 
```
The anomalies/outliers can be clearly spotted in the 'anomalies_flags' points.

[make-series](https://docs.microsoft.com/en-us/azure/data-explorer/time-series-analysis) <br>
[ADX Anomaly Detection](https://docs.microsoft.com/en-us/azure/data-explorer/anomaly-detection#time-series-anomaly-detection)

**FOR THE NEXT TASKS, WE WILL USE 'taxi' TABLE IN THE SAME DATABASE.**  <br>
Please follow this Azure Open Dataset on [NYC Taxi Rides](https://docs.microsoft.com/en-us/azure/open-datasets/dataset-taxi-yellow?tabs=azureml-opendatasets) to ingest this data into your ADX cluster.

#### Task 5: Get familiar with the new table and create a piechart
Write queries that you have written in the previous challenge to get familiar with this table. After some familiarity, write a query to create a piechart of the payments type. Use 'tostring' to convert the payment_type to string before rendering the piechart.

#### Task 6: Datetime operations
Write a query to create a columnchart which will show the number of rides for each day of the week, across the entire data set.  You can use 1, 2, ..., 7 to denote Sunday through Saturday.

[dayofweek() - Azure Data Explorer | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/dayofweekfunction)
  
Expected result:
  
![Screen capture 1](/assets/images/Challenge6-Task6-Pic1.png)

#### Task 7: Multiple series on the same timechart
Write a query to find out if the tip amount correlates with the number of passengers in the taxi between 1 July 2021 and 31 July 2021. Restrict the number of passengers to maximum of 4.

#### Task 8: Detect anomalies in the tip amount
Write a query to draw anomaly chart for the tip amount in the month of July 2021. <br>
Hint 1: make-series for the average tip amount, with 1 h steps <br>
Hint 2: Use series_decompose_anomalies with this series and parameter of 5 (sensitivity level)

Expected result:
  
  ![Screen capture 1](/assets/images/Challenge6-Task8-Pic1.png)

#### Task 9: Let's **join** the party
The taxi rides  table has a field of Payment_type. This is a numeric code signifying how the passenger paid for the trip. There is another table (payment_type_lookup) which contains mapping between the numeric code and the description of the payment type.

To start with, take 10 records and use leftouter join to merge the rows of the two tables to form a new table, by matching values of the payment code column.

What is the most common method of payment for rides? Credit cards or cash? What does it look like over time? 

Expected result:
  
  ![Screen capture 1](/assets/images/Challenge6-Task9-Pic1.png)
  
  
#### Task 10: Forecasting
Create a timechart that will show:
- The number of rides during July 2021
- A forecast of the number of drive-ins for the first week of August, based on July 2021 (Use the series_decompose_forecast function).

Hint: Start your query with:

  ```
let min_t = datetime(2021-07-01);
let max_t = datetime(2021-08-07); // Note that there is no data in the first week of August. We will forecast the data for this week.
taxi
| where tpep_dropoff_datetime between (min_t .. max_t) 
```
  
- Make a series of the number of rides, on tpep_pickup_datetime between these dates. Use steps of 30 minutes. 
- Use series_decompose_forecast with parameters of this series and second parameter of: 24*7 (The second parameter is an Integer specifying the number of points at the end of the series to predict (forecast). These points are excluded from the learning (regression) process. We will use 24*7 additional data points, in order to forecast a week forward).
- Once a series is created, you can render a timechart.

Expected result:
  
  ![Screen capture 1](/assets/images/Challenge6-Task10-Pic1.png)

### Challenge 7: Visualisation

#### Task 1: Prepare interactive dashboards with ADX Dashboard

Using Dashboard feature of Azure Data Explorer, build a dashboard using outputs of any 5 queries (on LogisticsTelemetryExtended table) that you have created in the previous challenges with the following improvements:
  - Add filter on the dashboard so that the user can choose the timespan
  - Add filter on the dashboard so that the user can choose the transportation mode

Include **filters for the dashboard** so that the queries do not need to be modified if the user wants to analyse the charts with different values of a parameter. For example, users would like to analyse the charts over the last week, the last 14 days as well as the last 1 month. Users would also like to analyse the charts by different transportation modes.

Hint 1: In the query window, explore the “Share” menu.
  
  ![Screen capture 1](/assets/images/Challenge7-Task1-Pic1.png)
 
- [Visualize data with the Azure Data Explorer dashboard | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/azure-data-explorer-dashboards)
- [Parameters in Azure Data Explorer dashboards | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/dashboard-parameters)

#### Task 2: Prepare management dashboard with PowerBI
Visualize the outputs of [Task 5](https://github.com/Azure/azure-kusto-microhack#task-5-get-familiar-with-the-new-table-and-create-a-piechart) and [Task 6](https://github.com/Azure/azure-kusto-microhack#task-6-datetime-operations) in Challenge 6 in PowerBI using the DirectQuery mode. 

Hint 1: In the query window, explore the “Share” menu.

There are multiple ways to connect ADX and PowerBI depending on the use case. For this Microhack, we will use the DirectQuery method. Feel free to explore other methods on the docs.

[Visualize data using the Azure Data Explorer connector for Power BI | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-explorer/power-bi-connector)

