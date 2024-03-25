# Measure names and measure values

When you add a measure to a chart section, two auxiliary fields are added to the dataset field list: `Measure names` and `Measure values`. They are missing in the original dataset field list, as {{ datalens-short-name }} creates them automatically. The `Measure names` and `Measure values` fields are used to create charts with multiple measures.

`Measure names` is a **dimension** (a green field) that includes **names** of all measures in the chart. It is used to group chart values or show measure names as legends. For example, you can use `Measure names` to build a bar chart grouped by multiple measures or to label sectors in a pie chart.

`Measure values` is a **measure** (blue field) that includes **values** of all measures in the chart. It is used to label values of each measure. For example, you can use `Measure values` to label each line in a chart or each column in a bar chart.

## Using measure names and measure values in charts {#usage}

Let's see some examples of how to use `Measure names` and `Measure values` in charts. As a data source, we will use a direct [connection](../../quickstart.md#create-connection) to a demo database; the dataset is based on the `SampleSuperstore` table.

**Example 1**

Create a pivot table with total sales across each product category by region.

![image](../../../_assets/datalens/concepts/measure-names-1.png)

Now, let's also use the table to show profit for each category and region. For this, drag the `Profit` field to **Measures**. The `Measure names` field will be added automatically to the **Columns** section. This way, you can group your chart by measure names.

![image](../../../_assets/datalens/concepts/measure-names-2.png)

You can edit grouping by table measure names. For this, drag the `Measure names` field to the **Rows** section.

![image](../../../_assets/datalens/concepts/measure-names-3.png)

**Example 2**

Let's use the graph to show monthly sales during a year.

![image](../../../_assets/datalens/concepts/measure-values-1.png)

Now let's add a second Y axis to show the profit.

![image](../../../_assets/datalens/concepts/measure-values-2.png)

Add labels with measure values to each line. The chart uses two measures, but you can only add one of them to the **Labels** section. To label each line in this case, add `Measure values` to **Labels**. Every line will be labeled by values of its measure.

![image](../../../_assets/datalens/concepts/measure-values-3.png)

**Example 3**

Compare the order count and average order value by region. Add the measures to the **Y** section to build a stacked bar chart. The `Measure names` field will be added automatically to the **Colors** section for grouping by measure name.

![image](../../../_assets/datalens/concepts/measure-names-4.png)

This is not the best way to compare measures, though. Showing an X axis grouped column chart would be a better idea. For this, drag the `Measure names` dimension to the **X** section.

![image](../../../_assets/datalens/concepts/measure-names-5.png)

To label each column with its measure name, add `Measure values` to the **Labels** section.

![image](../../../_assets/datalens/concepts/measure-names-6.png)

## Limitations {#restrictions}

The following restrictions apply to the `Measure names` and `Measure values` fields:

* You cannot use `Measure names` and `Measure values` to filter your chart.
* You can use `Measure values` to sort data only in the [{#T}](../../visualization-ref/area-chart.md) and [{#T}](../../visualization-ref/normalized-area-chart.md) charts after you add `Measure names` to the **Colors** section.
