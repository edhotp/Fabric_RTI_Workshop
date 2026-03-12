# Real-Time Intelligence tutorial part 7: Detect anomalies on an Eventhouse table

> [!NOTE]
> This tutorial is part of a series. For the previous section, see: [Real-Time Intelligence tutorial part 6: Create a Real-Time Dashboard](tutorial-6-create-dashboard).

Anomaly detection is a feature of Real-Time Intelligence that allows you to identify unusual patterns in your data. In this part of the tutorial, you learn how to create an 'Anomaly detector' item on your workspace to detect anomalies in the number of empty docks at a station.

## Detect anomalies on an Eventhouse table

1. From the left navigation bar, select **Real-Time** to open the *Real-Time hub*.
2. Under **All data streams** select the eventhouse table **TransformedData** you created in the previous tutorial. The table details page opens. Select **Detect anomalies** from the top menu.

    [![Screenshot of eventhouse table details page and detect anomalies selected.](media/tutorial/detect-anomalies.png)](media/tutorial/detect-anomalies.png#lightbox)
3. Enter **`BikeAnomaliesconfiguration`** as Name.
4. Under Save to, select **Create detector**.
5. Select the workspace in which you want to create the anomaly detector item, enter **`BikeAnomalies`**. Then select **Create**.
6. In the *Select attributes* section, choose the following options:

    | Field | Value |
    | --- | --- |
    | Value to watch | No\_Empty\_Docks |
    | Group by | Street |
    | Timestamp | Timestamp |

    [![Screenshot of anomaly configuration pane.](media/tutorial/anomaly-configuration.png)](media/tutorial/anomaly-configuration.png#lightbox)
7. Select **Run analysis**.

    > [!IMPORTANT]
    > Analysis typically takes up to 4 minutes depending on your data size and can run for up to 30 minutes. You can navigate away from the page and check back in when the analysis is complete.

    > [!NOTE]
    > Ensure your Eventhouse table contains sufficient historical data to improve model recommendations and anomaly detection accuracy. For example, datasets with one data point per day require a few months of data, while datasets with one data point per second might only need a few days.
8. When analysis is complete, anomalies along with tabular data are displayed on the right.

    [![Screenshot of completed anomaly detection.](media/tutorial/anomalies-detected.png)](media/tutorial/anomalies-detected.png#lightbox)

    > [!NOTE]
    > Play around with the **Detection model** under **Customize detection** section and Timestamp above the **Detector results** pane. More data might increase anomaly detection accuracy.
9. Select **Save**.
