# Real-Time Intelligence tutorial part 5: Query streaming data using KQL

> [!NOTE]
> This tutorial is part of a series. For the previous section, see: [Real-Time Intelligence tutorial part 4: Transform data in a KQL database](tutorial-4-transform-kql-database).

In this part of the tutorial, you query streaming data using a few different methods. You write a KQL query to visualize data in a time chart and you create an aggregation query using a materialized view. You also query data by using T-SQL and by using `explain` to convert SQL to KQL. Finally, you use Copilot to generate a KQL query.

## Write a KQL query

The name of the table you created from the update policy in a previous step is *TransformedData*. Use this table name (case-sensitive) as the data source for your query.

- In the Tutorial\_queryset, enter the following query, and then press **Shift + Enter** to run the query.

    ```kusto
    TransformedData
    | where BikepointID > 100 and Neighbourhood == "Chelsea"
    | project Timestamp, No_Bikes
    | render timechart
    ```

    This query creates a time chart that shows the number of bikes in the Chelsea neighborhood as a time chart.

    [![Screenshot of bikes timechart in Real-Time Intelligence.](media/tutorial/bikes-timechart.png)](media/tutorial/bikes-timechart.png#lightbox)

## Create a materialized view

In this step, you create a materialized view, which returns an up-to-date result of the aggregation query. Querying a materialized view is faster than running the aggregation directly over the source table.

1. Copy and paste, then run the following command to create a materialized view that shows the most recent number of bikes at each bike station.

    ```kusto
    .create-or-alter materialized-view with (folder="Gold") AggregatedData on table TransformedData
    {
       TransformedData
       | summarize arg_max(Timestamp,No_Bikes) by BikepointID
    }
    ```
2. Copy and paste, then run the following query to see the data in the materialized view as a column chart.

    ```kusto
    AggregatedData
    | sort by BikepointID
    | render columnchart with (ycolumns=No_Bikes,xcolumn=BikepointID)
    ```

    [![Screenshot of the materialized view visualized as a column chart.](media/tutorial/tutorial-materialized-view.png)](media/tutorial/tutorial-materialized-view.png#lightbox)

You use this query in a later step to create a real-time dashboard.

> [!IMPORTANT]
> If you missed any of the steps used to create the tables, update policy, function, or materialized views, use this script to create all required resources: [Tutorial commands script](https://github.com/microsoft/fabric-samples/blob/main/docs-samples/real-time-intelligence/tutorial-commands-script.kql).

## Query using T-SQL

The query editor supports the use of T-SQL.

- Enter the following query, and then press **Shift + Enter** to run the query.

    ```kusto
    SELECT top(10) *
    FROM AggregatedData
    ORDER BY No_Bikes DESC
    ```

    This query returns the top 10 bike stations with the most bikes, sorted in descending order.

    | BikepointID | Timestamp | No\_Bikes |
    | --- | --- | --- |
    | 193 | 2025-12-29 13:40:58.760 | 39 |
    | 602 | 2025-12-29 13:40:53.009 | 34 |
    | 229 | 2025-12-29 13:40:56.510 | 32 |
    | 738 | 2025-12-29 13:40:56.510 | 32 |
    | 313 | 2025-12-29 13:40:53.009 | 30 |
    | 706 | 2025-12-29 13:40:58.760 | 27 |
    | 460 | 2025-12-29 13:40:53.009 | 27 |
    | 522 | 2025-12-29 13:40:53.009 | 26 |
    | 357 | 2025-12-29 13:40:53.009 | 25 |
    | 166 | 2025-12-29 13:40:58.760 | 24 |

## Convert a SQL query to KQL

To get the equivalent KQL for a T-SQL SELECT statement, add the keyword `explain` before the query. The output shows the KQL version of the query, which you can copy and run in the KQL query editor.

- Enter the following query. Then press **Shift + Enter** to run the query.

    ```kusto
    explain
    SELECT top(10) *
    FROM AggregatedData
    ORDER BY No_Bikes DESC
    ```

    This query returns a KQL equivalent of the T-SQL query you enter. The KQL query appears in the output pane. Try copying and pasting the output, and then run the query. This query might not be written in optimized KQL.

    ![Screenshot of the SQL to KQL conversion.](media/tutorial/tutorial-explain-sql.png)

## Use Copilot to generate a KQL query

If you're new to writing KQL, you can ask a question in natural language and Copilot generates the KQL query for you.

1. Select **Queryset** from the menu bar.
2. In the KQL queryset, select the **Copilot** icon from the menu bar.

    ![Screenshot of how to get to the right copilot.](media/tutorial/copilot-select.png)
3. Enter a question in natural language. For example, "Which station has the most bikes right now. Use the materialized view for the most updated data." It can help to include the name of the materialized view in your question.

    The Copilot suggests a query based on your question.
4. Select the **Insert** button to add the query to the KQL editor.

    [![Screenshot of Copilot dialog showing a generated KQL query and the Insert button.](media/tutorial/copilot.png)](media/tutorial/copilot.png#lightbox)
5. Select **Run** to run the query.

Ask follow-up questions or change the scope of your query. Use this feature to learn KQL and generate queries quickly.
