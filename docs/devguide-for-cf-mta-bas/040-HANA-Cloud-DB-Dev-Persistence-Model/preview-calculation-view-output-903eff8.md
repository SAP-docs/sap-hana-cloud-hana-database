<!-- loio903eff885ebd4c5cadb1e0c3e58f681d -->

# Preview Calculation View Output

After modeling calculation views based on your requirements, you can deploy them and preview their output.



## Context

You can preview output data of calculation views in simple tabular format, or you can preview output data in graphical representations such as, bar graphs, area graphs, and pie charts. If your calculation view is defined with hierarchies, and the hierarchies are deployed as SQL hierarchy views, the tool allows you to preview the output data in hierarchical representations.

You can also export and download the output data to `.csv` files. The tool also allows you to preview the SQL query that the tool executed to fetch the output data.



## Procedure

1.  Start SAP Business Application Studio.

    You can preview calculation view data from the SAP HANA Database Explorer or from the Business Application Studio.

2.  Preview calculation view data from the SAP HANA Database Explorer
3.  From Business Application Studio, go to the HANA project explorer.

    1.  Select the database connection, then click the *Open HDI Container* icon.

        Alternatively, from the command palette:

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press  [F1\]  or
        -   Choose *View* \> *Find Command...*

    2.  Locate and run *SAP HANA: Open Database Explorer*

        If prompted, provide your login credentials.

    3.  Expand the container node in the SAP HANA Database Explorer.

    4.  Choose *Column Views* in the list of object types.

    5.  Check the calculation view is listed in the results pane.

    6.  Select the calculation view to display the contents in the details pane.


4.  Preview calculation view data from the Business Application Studio
5.  Go to the last node below *Semantics*, then choose *Data Preview* from the context menu.

    To preview output data of the calculation view with the user of a different Database Explorer connection, choose *Data Preview With Other Database User*.

    > ### Note:  
    > When a data preview is started, by default, a query that includes all columns and no filters is executed. This can lead to long runtimes and high resource consumption, which is not necessary if you are only interested in data in specific columns.
    > 
    > You can disable this automatic query execution. Then, to request data in the *Raw* tab of the data preview, do a manual refresh.
    > 
    > To disable automatic refresh, choose *File* \> *Preferences* \> *Open Preferences*.
    > 
    > For the option: *Watt Feature › Calculation View Editor: Data Preview: Require Manual Refresh For Raw Data*, select *Require manual refresh of data when opening a table or view, and when visualizing its data in the Analysis tab*.

6.  Provide an input parameter or variable value.

    If you have defined any input parameters in the calculation view, provide the required input parameter values as follows:

    1.  Select the required operator.

    2.  Provide values for the *From* and *To* fields based on the selected operator.

    3.  In the toolbar, choose *Open Content*.

        In the *Raw Data* tab, the tool displays the output data in tabular format.


7.  \(Optional\) Apply filters.

    1.  If you want to apply filters on columns and preview the filtered output data, in the toolbar, choose ![](images/Filter_f553f3d.png) \(Add Filter\).

    2.  Choose *Add Filters*.

    3.  Select the required columns and define the filter conditions.

    4.  Choose *Apply*.


8.  Export output data, if required.

    If you want to export the raw data output to a .csv file, perform the following steps:

    1.  In the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\).

    2.  In the *Delimiter* drop-down list, select the required delimiter that the tool must use to separate the values in the `.csv` file.

    3.  Choose *Download*.


9.  View the SQL query used by the calculation view, if required.

    1.  To view the SQL query that the tool executed to fetch the data, in the toolbar, choose *SQL*.

    2.  To view, edit and execute the SQL query in SQL editor, choose ![](images/SQL_9bdadeb.png) \(Edit SQL Statement in SQL Console\).


10. Preview the output of a calculation view in graphical format.

    You can preview the output of a calculation view as a bar graph, an area graph, a pie chart, or as a table chart, as well as in other graphical representations. These graphical representations allow more detailed analysis of output data.

    1.  In the menu bar, choose *Analysis*.

    2.  Configure the axis values by dragging and dropping the required attributes and measures to the *Label Axis* and the *Value Axis*.

        The tool displays the output data in graphical representation. Select the required chart icons in the menu to view the output in different graphical representation.

    3.  In the toolbar, choose ![](images/Settings_DataPreview_e220dd1.png) \(Display Settings\) to toggle legends and values.

    4.  If you want to view the query SQL query that the tool executed to fetch the data for the provided axes configurations, in the toolbar, choose *SQL*.

    5.  If you want to export the charts as `.png` files to your local system, in the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\) and select *Chart*.

    6.  If you want to export the raw output data as `.csv` files to your local system, in the toolbar, choose ![](images/Download_30e7d1e.png) \(Download\) and select *Data*.



**Related Information**  


[Create Calculation Views](create-calculation-views-5aeb56c.md "Use a graphical editor to create calculation views that depict a complex business scenario.")

