<!-- loio5aeb56cba39e4df4ae62b43a0dc2fad4 -->

# Create Calculation Views

Use a graphical editor to create calculation views that depict a complex business scenario.



## Context

Calculation views can be used to combine data from various sources. You can combine multiple transaction tables in a calculation view. You can also create calculation views to include layers of calculation logic.



## Procedure

1.  To create a calculation view:
2.  Start SAP Web IDE Full-Stack.

3.  To create a new project for the calculation view, do the following:

    1.  In the SAP Web IDE, choose *File* \> *New* \> *Project from Template*.

    2.  In the *Environment* dropdown list, select *Cloud Foundry*.

    3.  Select *Multi-Target Application Project* and choose *Next*.

    4.  Type a name for the new MTA project \(for example, ***myApp***\), then choose *Next* to confirm.

    5.  Specify details of the new MTA project and choose *Next* to confirm.

    6.  Create the new MTA project; choose *Finish*.


4.  Create a new calculation view artifact.

    Browse to the *src* folder, right-click it and choose *New* \> *Calculation View*.

5.  Enter the details for the new calculation view.

    1.  In the *Name* field, enter the name of the calculation view.

    2.  In the *Data Category* dropdown list, select a value.


6.  Choose *Create*.

    The calculation view editor is opened. Depending on the data category that you selected when you created the calculation view, the default view node can be an aggregation or a projection view node. If you are creating a calculation view with star join, the default view node is a star join view node.

    > ### Note:  
    > You can switch between the default view nodes. For example, to switch from a default aggregation view node to a projection view node or a star join view node, right-click the default view node and select the required menu option.

7.  Continue modeling the calculation view by selecting view nodes from the tool palette and adding them to the view editor.

    To switch between any of the inner aggregation or projection view nodes, right-click the view node and select the required menu option.

8.  Add data sources.

    To add data sources to the view node:

    1.  Select a view node.

    2.  In the editor toolbar, choose ![](images/details_5b34943.png) \(Expand Details Panel\).

    3.  Choose ![](images/Add_Data_Sources_1689131.jpg) \(Add Data Source\).

    4.  In the *Find Data Sources* dialog box, select the type of the data source.

    5.  Enter the name of the data source and select it from the list.

        You can add one or more data sources depending on the selected view node.

    6.  Choose *Finish*.

        > ### Note:  
        > Supported data sources in view nodes in the current version.
        > 
        > The *Find Data Sources* dialog box displays multiple object types in the search result. But, depending on the selected view node, you can only add one object, such as activated \(built\) catalog tables, calculation views, SQL views, and table functions as data sources in the view nodes.


9.  \(Optional\) Add data sources from external services \(HDI or non-HDI containers\).

    You can use synonyms to access objects from non-HDI containers or from HDI containers. The tool automatically creates \(or modifies the existing\) `.hdbsynonym`, `.hdbgrants`, and `.hdbsynonymconfig` \(which is created in `cfg` folder for objects in HDI\), files that are necessary to consume the synonym.

    > ### Note:  
    > You can access data sources from external services only if you have created the necessary user-provided service and configured it in the `mta.yaml` file.
    > 
    > For more information see, *Consume Objects That are not Included in Your Development Project*.

    1.  Select a view node.

    2.  Choose ![](images/Add_Data_Sources_1689131.jpg) \(Add Data Source\).

        The *Find Data Sources* dialog box appears.

    3.  In the *External Services* drop-down list, select the required external service.

    4.  Enter the name of the data source you want to access from the external service and select it from the search list.

        You can add one or more data sources depending on the selected view node.

    5.  If no synonym exists for the target object, choose *Create Synonym*.

        If a synonym already exists for the target object, choose *Finish*.

    6.  \(Optional\) Modify the synonym name.

    7.  Define the object owner role and the application user role.


        <table>
        <tr>
        <th valign="top">

        Object Type


        
        </th>
        <th valign="top">

        Steps


        
        </th>
        </tr>
        <tr>
        <td valign="top">

        Objects in HDI Containers


        
        </td>
        <td valign="top">

        If the selected object is from a HDI container:

        1. In the *Object Owner Role*, enter the name of the object owner role.

        2. In the *Application User Role*, enter the name of the application user role.

        For more information on roles for HDI containers, see the topic, *Roles \(.hdbrole\)* in the *SAP HANA Cloud Deployment Infrastructure \(HDI\) Reference*.

        If the object for which you are creating the synonym is in a HDI container, select *Synonym for HDI Container*. This selection helps the tool identify that you are creating synonym for an object in the HDI container.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        Objects in non HDI containers


        
        </td>
        <td valign="top">

        If the selected object is from a HDI container:

        1. In the *Object Owner Role*, enter the name of the object owner role.

        2. In the *Application User Role*, enter the name of the application user role.

        For more information on roles for non-HDI containers, see the topic, *Enable Access to Objects in a Remote Classic Schema* in the *SAP HANA Cloud Deployment Infrastructure \(HDI\) Reference*.


        
        </td>
        </tr>
        </table>
        
    8.  Choose *Finish*.

        The synonym is created, along with the `.hdbsynonym`, `.hdbgrants`, and `.hdbsynonymconfig` \(which is created in `cfg` folder for objects in HDI\) files in the same SAP HANA Database Module.


10. Define output columns.

    1.  Select a view node.

    2.  In the editor toolbar, choose ![](images/details_5b34943.png) \(Expand Details Panel\).

    3.  On the *Mapping* tab, select the column you want to add to the output.

    4.  In the context menu, choose *Add To Output*.

    5.  To add all columns in a data source to the output, from the context menu of the data source, select *Add To Output.*

        > ### Note:  
        > Using keep flag property. The *Keep Flag* property on attribute columns influence the result set. Use *Keep Flag* property, for example, to aggregate the measures by performing an SQL `GROUP BY` operation on them, even when they are not included in the query.
        > 
        > 1.  Select the view node.
        > 2.  On the *Mapping* tab, select an output column.
        > 3.  In the *Properties* section, set the value of *Keep Flag* property to *True*.


11. Define attributes and measures.

    To successfully activate a calculation view with data category CUBE, you must specify at least one column as a measure.

    1.  Select the *Semantics* view node.

    2.  On the *Columns* tab, select a column value.

    3.  In the *Type* drop-down list, select *Measure* or *Attribute*.

        If the data category is set to CUBE, an additional aggregation column is available to specify the aggregation type for measures.


12. \(Optional\) Copy a calculation view.

    You can copy a calculation view and paste it using a different name within the same or different SAP HANA Database module. In the view properties, the calculation view ID is automatically adjusted.

    1.  In the Workspace view, right-click the calculation view.

    2.  Choose *Copy*.

    3.  Right-click on the target folder and choose *Edit* \> *Paste*.

    4.  Provide a new name.

    5.  Choose *OK*.


13. \(Optional\) View modeler objects in the outline pane.

    Use the *Outline* pane in SAP Web IDE to obtain a quick overview of the modeler objects \(view nodes and columns\) in the calculation view.

    1.  In the menu bar, choose *View* \> *Outline*.

        All the modeler objects are displayed in the calculation view. You can also select an object in the outline pane, and navigate to the editor to identify where the object is used in the calculation view.

    2.  In the right menu bar, choose ![](images/Outline_Pane_137600d.jpg) \(Outline\) to show or hide the outline pane.


14. Choose *Save* on the menu bar to save your calculation view.

15. Build an SAP HANA Database Module.

    In the HANA project explorer, select the module and choose *Deploy*.

    The build process uses the design-time database artifacts to generate the corresponding actual objects \(runtime objects\) in the HDI container.




## Next Steps

After creating a calculation view, you can modify the output to your needs. The following table shows how you can modify the calculation view.

<a name="loio5aeb56cba39e4df4ae62b43a0dc2fad4__table_agw_wxc_xp"/>Working With View Nodes


<table>
<tr>
<th valign="top">

Requirement



</th>
<th valign="top">

Task to Perform



</th>
</tr>
<tr>
<td valign="top">

Query data from two data sources and combine records from both the data sources, based on a join condition, or to obtain language-specific data.



</td>
<td valign="top">

Create Joins



</td>
</tr>
<tr>
<td valign="top">

Combine the results of two or more data sources.



</td>
<td valign="top">

Create Unions



</td>
</tr>
<tr>
<td valign="top">

Partition the data for a set of partition columns, and perform an order by SQL operation on the partitioned data.



</td>
<td valign="top">

Create Rank Nodes



</td>
</tr>
<tr>
<td valign="top">

Perform intersect set operations on two data sources.



</td>
<td valign="top">

Use Intersect Set Operation



</td>
</tr>
<tr>
<td valign="top">

Perform minus set operations on two data sources.



</td>
<td valign="top">

Use Minus Set Operation



</td>
</tr>
<tr>
<td valign="top">

Model calculation views with SAP HANA hierarchy functions.



</td>
<td valign="top">

Use Hierarchy Functions



</td>
</tr>
<tr>
<td valign="top">

Model table functions in calculation views with both tabular input parameters and scalar input parameters.



</td>
<td valign="top">

Model Table Functions as View Nodes



</td>
</tr>
<tr>
<td valign="top">

Filter the output of view nodes.



</td>
<td valign="top">

Filter Output of View Nodes.



</td>
</tr>
<tr>
<td valign="top">

Use a form-based editor to create virtual tables.



</td>
<td valign="top">

Create Virtual Tables



</td>
</tr>
</table>

<a name="loio5aeb56cba39e4df4ae62b43a0dc2fad4__table_fkj_12f_fs"/>Working With Columns


<table>
<tr>
<th valign="top">

Requirement



</th>
<th valign="top">

Task to perform



</th>
</tr>
<tr>
<td valign="top">

Count the number of distinct values for a set of attribute columns.



</td>
<td valign="top">

Create Counters



</td>
</tr>
<tr>
<td valign="top">

Create new output columns and calculate their values at run time using an expression.



</td>
<td valign="top">

Create Calculated Columns



</td>
</tr>
<tr>
<td valign="top">

Assign semantic types to provide more meaning, and to attach information about the type of attributes and measures in calculation views.



</td>
<td valign="top">

Assign Semantics



</td>
</tr>
<tr>
<td valign="top">

Parameterize calculation views and execute them based on the values users provide at query run time.



</td>
<td valign="top">

Create Input Parameters



</td>
</tr>
<tr>
<td valign="top">

Filter the results based on the values that users provide to attributes at run time.



</td>
<td valign="top">

Assign Variables



</td>
</tr>
<tr>
<td valign="top">

Create level hierarchies to organize data in reporting tools.



</td>
<td valign="top">

Create Level Hierarchies



</td>
</tr>
<tr>
<td valign="top">

Create parent-child hierarchies to organize data in reporting tools.



</td>
<td valign="top">

Create Parent-Child Hierarchies



</td>
</tr>
<tr>
<td valign="top">

Associate measures with currency codes and perform currency conversions.



</td>
<td valign="top">

Associate Measures with Currency



</td>
</tr>
<tr>
<td valign="top">

Associate measures with unit of measures and perform unit conversions.



</td>
<td valign="top">

Associate Measures with Unit of Measure



</td>
</tr>
<tr>
<td valign="top">

Define data masking for column values when modeling a calculation view.



</td>
<td valign="top">

Mask Column Values in Client Tools



</td>
</tr>
<tr>
<td valign="top">

Define default values for columns \(both attributes and measures\).



</td>
<td valign="top">

Handle Null Values in Columns



</td>
</tr>
<tr>
<td valign="top">

Group related measures and related attributes together in a folder.



</td>
<td valign="top">

Group Related Measures and Attributes



</td>
</tr>
</table>

<a name="loio5aeb56cba39e4df4ae62b43a0dc2fad4__table_zql_12f_fs"/>Working With Calculation View Properties


<table>
<tr>
<th valign="top">

Requirement



</th>
<th valign="top">

Task to perform



</th>
</tr>
<tr>
<td valign="top">

Filter the view data either using a fixed client value or using a session client set for the user.



</td>
<td valign="top">

Filter Data for Specific Clients



</td>
</tr>
<tr>
<td valign="top">

Discourage use of a calculation view.



</td>
<td valign="top">

Deprecate Calculation Views



</td>
</tr>
</table>

**Related Information**  


[Working With View Nodes](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/20ad4018a0ab4f2f84968beb8ab521e2.html "View nodes are the building blocks of calculation views.") :arrow_upper_right:

[Preview Calculation View Output](preview-calculation-view-output-903eff8.md "After modeling calculation views based on your requirements, you can deploy them and preview their output.")

[Working With Attributes and Measures](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/8493c7f54a3b4b728821ecee972e2963.html "Attributes and measures form content data that you use for data modeling. Attributes represent the descriptive data, such as product or a region, and measures represent quantifiable data, such as revenue or quantity sold.") :arrow_upper_right:

[Working With Calculation View Properties](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/9774a676c8fe46c79c5b197051fa9743.html "While modeling calculation views, you can define certain properties for the calculation views so that the tool can refer to those values and run the view respectively.") :arrow_upper_right:

[Additional Functionality for Calculation Views](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/a19aa4797aea4eb0b402aef360a4e14f.html "After modeling a calculation view or during design time, you can use additional functions to better understand the performance of the view at runtime and to more efficiently model calculation views.") :arrow_upper_right:

[Defining Data Access Privileges](defining-data-access-privileges-acd7703.md "Use the analytic privilege editor in SAP Web IDE Full-Stack to create analytic privileges.")

[Create Calculation Views with Star Joins](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/988f5a9bd87c4492ad5c1e6f7936f0b5.html "Star joins connect a central data entity to multiple entities that are logically related. You can create a calculation view with star joins that join multiple dimensions to a single fact table.") :arrow_upper_right:

[Create Calculation Views with Time Dimension](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/5a787289ee7e4f7fad10f0f5dfd54646.html "You can add time dimensions to a calculation view by using the standard time-related tables as data sources in the calculation view.") :arrow_upper_right:

[Example: Using Keep Flag](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/f0e101a7641340708f0b098206210d9c.html "The Keep Flag option for attribute columns influences the result set of a calculation view.") :arrow_upper_right:

[Create Virtual Tables](create-virtual-tables-00340d4.md "Virtual tables enable you to access objects in other databases without having to replicate in SAP HANA.")

[Consume Objects That are not Included in Your Development Project](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2022_2_QRC/en-US/9c5e5d49af274281b74062a87d5cb34e.html "To consume objects that are not included in your project (or in your HDI container), you need to define synonyms that point to the objects that you wish to consume.") :arrow_upper_right:
