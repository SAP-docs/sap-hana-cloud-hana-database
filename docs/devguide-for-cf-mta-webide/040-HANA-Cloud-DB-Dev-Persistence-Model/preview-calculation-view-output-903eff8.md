<!-- loio903eff885ebd4c5cadb1e0c3e58f681d -->

# Preview Calculation View Output

After you have modeled a calculation view, you can deploy it and preview its output.



## Context

You can preview output data of calculation views in simple tabular format, or you can preview output data as graphical representations, such as bar graphs or pie charts. If your calculation view is defined with hierarchies, and the hierarchies are deployed as SQL hierarchy views, you can preview the output data as hierarchical representations.

You can also download the output data to `.csv` files.



<a name="loio903eff885ebd4c5cadb1e0c3e58f681d__steps_nrx_ggl_qyb"/>

## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  In the *Workspace* view, select a calculation view to preview its output.

3.  In the context menu, choose *Data Preview*.

4.  Provide an input parameter or variable value.

    If you have defined any input parameters in the calculation view, provide the input parameter values as follows:

    1.  Select the operator.

    2.  Specify values for the *From* and *To* fields, based on the selected operator.

    3.  In the toolbar, choose ![](images/Open_Content_28e1183.jpg) \(Open Content\).

        In the *Raw Data* tab, the output data is displayed.


5.  \(Optional\) Apply filters.

    1.  To apply filters on columns and preview the filtered output data, in the toolbar, choose ![](images/Filter_f553f3d.png) \(Add Filter\).

    2.  Choose *Add Filters*.

    3.  Select the required columns and define the filter conditions.

    4.  Choose *Apply*.


6.  Export output data, if required.

    To export the raw data output to a `.csv` file:

    1.  In the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\).

    2.  In *Delimiter*, select the delimiter to be used to separate the values in the `.csv` file.

    3.  Choose *Download*.


7.  View the SQL query used by the calculation view.

    1.  To view the SQL query that the tool executed to fetch the data, in the toolbar, choose *SQL*.

    2.  To view, edit, and execute the SQL query in SQL editor, choose ![](images/SQL_9bdadeb.png) \(Edit SQL Statement in SQL Console\).


8.  Preview the output of a calculation view in graphical format.

    You can preview the output of a calculation view as a bar graph, an area graph, a pie chart, or as a table chart, as well as in other graphical representations. These graphical representations allow more detailed analysis of output data.

    1.  In the menu bar, choose *Analysis*.

    2.  Configure the axis values by dragging and dropping the required attributes and measures to the *Label Axis* and the *Value Axis*.

        The tool displays the output data. Select the required chart icons in the menu to view the output.

    3.  In the toolbar, choose ![](images/Settings_DataPreview_e220dd1.png) \(Display Settings\) to toggle legends and values.

    4.  To view the SQL query that the tool executed to fetch the data for the axis configurations, in the toolbar, choose *SQL*.

    5.  To export the charts as `.png` files to your local file system, in the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\) and select *Chart*.

    6.  To export the raw output data as `.csv` files to your local file system, in the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\) and select *Data*.


    > ### Note:  
    > You can also preview the data as it is processed at a specific node. Right-click the node, and choose *Data Preview*.

9.  Preview output of hierarchies.

    SAP Database Explorer provides a *Hierarchies* tab to preview output of calculation views that contain hierarchies. If you have defined any hierarchies in calculation views of type Dimension or Cube, you can preview output in hierarchical tree structures.

    > ### Note:  
    > SAP Database Explorer does not support preview output of compound parent-child hierarchies in calculation views.

    1.  In the menu bar, go to the *Hierarchies* tab.

        The *Available Objects* pane displays all the hierarchies defined in the calculation view, including hierarchies from shared dimensions. It also displays the measures defined in the calculation view.

    2.  Drag and drop a hierarchy to the *Selected Hierarchy* pane.

        > ### Restriction:  
        > Preview of multiple hierarchies at the same time is not supported. You can preview output in hierarchical tree structure of only one hierarchy at a time.

    3.  \(Optional\) To preview the output with one or more measures from the calculation view, drag and drop the measure to the *Selected Measure\(s\)* pane.

        The output data is built in a hierarchical tree structure for the selected configuration. The root node is expanded and the number of records displayed depends on the SQL console settings.

    4.  If you are previewing output of a calculation view \(type dimension\) and if you want to view the SQL query that the tool executed on the tables to fetch the output data, in the toolbar, choose *SQL*.

    5.  To export the output data to a `.csv` file, in the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\).


10. \(Optional\) Preview output of intermediate nodes.

    If you have activated the calculation view, you can also preview the output of any of its intermediate view nodes. This preview helps know the output data that is passed to the higher view node levels.

    1.  Switch to the *Development* perspective.

    2.  In the *Workspace* view, select a calculation view and open it in the view editor.

    3.  Right-click the intermediate view node and choose *Data Preview*.



**Related Information**  


[Data Analysis](https://help.sap.com/viewer/d625b46ef0b445abb2c2fd9ba008c265/2024_1_QRC/en-US/42beb7bab4484130958ef62ee7b031aa.html "After you have modeled a calculation view, you can analyze its output.") :arrow_upper_right:

[Configuring Data Preview Behavior](https://help.sap.com/viewer/d625b46ef0b445abb2c2fd9ba008c265/2024_1_QRC/en-US/92883c2b13c74649b183590c4b5744ae.html "You can configure different preview options.") :arrow_upper_right:

[Create Calculation Views](create-calculation-views-5aeb56c.md "Use a graphical editor to create calculation views that depict complex business scenarios.")

