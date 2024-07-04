<!-- loio903eff885ebd4c5cadb1e0c3e58f681d -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Preview Calculation View Output

After you have modeled a calculation view, you can deploy it and preview its output.



## Context

You can preview output data of calculation views in simple tabular format, or you can preview output data as graphical representations, such as bar graphs or pie charts. If your calculation view is defined with hierarchies, and the hierarchies are deployed as SQL hierarchy views, you can preview the output data as hierarchical representations.

You can also download the output data to `.csv` files.



<a name="loio903eff885ebd4c5cadb1e0c3e58f681d__steps_nrx_ggl_qyb"/>

## Procedure

1.  Start SAP Business Application Studio.

    You can preview calculation-view data either in SAP HANA Database Explorer or in SAP Business Application Studio.

2.  Preview calculation-view data from SAP HANA Database Explorer.

    1.  In SAP Business Application Studio, open the SAP HANA Projects explorer.

    2.  Select a database connection, then choose *Open HDI Container*.

        Alternatively, from the command palette:

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\]  or
        -   Choose *View* \> *Command Palette...*

    3.  Locate and run *SAP HANA: Open Database Explorer*

        If prompted, provide your login credentials.

    4.  Expand the container node in SAP HANA Database Explorer.

    5.  Choose *Column Views* in the list of object types.

    6.  Check the calculation view is listed in the results pane.

    7.  Right-click the calculation view and choose *Open Data* from the context menu in the *Catalog Browser*.


3.  Preview calculation view data from SAP Business Application Studio

    Go to the last node below *Semantics*, then choose one of the following options from the context menu.


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Result
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Data Preview* 
    
    </td>
    <td valign="top">
    
    Starts a data preview.

    You can choose between *Raw Data* and *Analysis*. If available, hierarchies are also shown.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Data Preview With Other Database User* 
    
    </td>
    <td valign="top">
    
    Starts a data preview with a different database user.

    Only connections that are defined in Database Explorer are available.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *SQL Editor* 
    
    </td>
    <td valign="top">
    
    Shows the `SELECT` statement in the SQL Console.

    From here, you can edit the statement.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > When a data preview is started, by default, a query that includes all columns and no filters is executed. This can lead to long run times and high resource consumption, which is not necessary if you are only interested in data in one or more specific columns. For more information about how to disable automatic query execution, see *Configuring Data-Preview Behavior* in *Related Information* below.

4.  Provide an input parameter or variable value.

    If you have defined any input parameters in the calculation view, provide the input parameter values as follows:

    1.  Select the operator.

    2.  Specify values for the *From* and *To* fields, based on the selected operator.

    3.  In the toolbar, choose *Open Content*.

        In the *Raw Data* tab, the output data is displayed.


5.  **Optional:** Apply filters.

    1.  To apply filters on columns and preview the filtered output data, in the toolbar, choose <span class="SAP-icons-V4"></span> \(Add Filter\).

    2.  Choose *Add Filter*.

    3.  Select the required columns and define the filter conditions.

    4.  Choose *Apply*.


6.  Export output data, if required.

    To export the raw data output to a `.csv` file:

    1.  In the toolbar, choose <span class="SAP-icons-V4"></span> \(Download\).

    2.  In *Delimiter*, select the delimiter to be used to separate the values in the `.csv` file.

    3.  Choose *Download*.


7.  View the SQL query used by the calculation view.

    1.  To view the SQL query that the tool executed to fetch the data, in the toolbar, choose *SQL* *\(Show/Hide the Current SQL Statement\)*.

    2.  To view, edit, and execute the SQL query in SQL editor, choose <span class="SAP-icons-V4"></span> *SQL* *\(Edit SQL Statement in SQL Console\)*.


8.  Preview the output of a calculation view in graphical format.

    You can preview the output of a calculation view as a bar graph, an area graph, a pie chart, or as a table chart, as well as in other graphical representations. These graphical representations allow more detailed analysis of output data.

    1.  In the menu bar, choose *Analysis*.

    2.  Configure the axis values by dragging and dropping the required attributes and measures to the *Label Axis* and the *Value Axis*.

        The tool displays the output data. Select the required chart icons in the menu to view the output.

    3.  In the toolbar, choose :gear: to toggle legends and values.

    4.  To view the SQL query that the tool executed to fetch the data for the axis configurations, in the toolbar, choose *SQL* *\(Show SQL Query\)*.

    5.  To export the charts as `.png` files to your local file system, in the toolbar, choose <span class="SAP-icons-V4"></span> \(Export\) and then *Chart*.

    6.  To export the raw output data as `.csv` files to your local file system, in the toolbar, choose <span class="SAP-icons-V4"></span> \(Export\) and then *Data*.


    > ### Note:  
    > You can also preview the data as it is processed at a specific node. Right-click the node, and choose *Data Preview*.

9.  **Optional:** Preview output of intermediate nodes.

    If you have activated the calculation view, you can also preview the output of any of its intermediate view nodes. This preview helps know the output data that is passed to the higher view node levels.

    To start an intermediate data preview in SAP Business Application Studio, choose a data preview action from the context menu of the node.


**Related Information**  


[Data Analysis](https://help.sap.com/viewer/d625b46ef0b445abb2c2fd9ba008c265/2024_3_QRC/en-US/42beb7bab4484130958ef62ee7b031aa.html "After you have modeled a calculation view, you can analyze its output.") :arrow_upper_right:

[Configuring Data Preview Behavior](https://help.sap.com/viewer/d625b46ef0b445abb2c2fd9ba008c265/2024_3_QRC/en-US/92883c2b13c74649b183590c4b5744ae.html "You can configure different preview options.") :arrow_upper_right:

[Create Calculation Views](create-calculation-views-5aeb56c.md "Use a graphical editor to create calculation views that depict complex business scenarios.")

