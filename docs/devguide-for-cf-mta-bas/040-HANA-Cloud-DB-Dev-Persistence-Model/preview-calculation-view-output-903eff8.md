<!-- loio903eff885ebd4c5cadb1e0c3e58f681d -->

# Preview Calculation View Output

After you have modeled a calculation view, you can deploy it and preview its output.



## Context

You can preview output data of calculation views in simple tabular format, or you can preview output data as graphical representations, such as bar graphs or pie charts. If your calculation view is defined with hierarchies, and the hierarchies are deployed as SQL hierarchy views, you can preview the output data as hierarchical representations.

You can also download the output data to `.csv` files.

You can preview calculation view data from SAP HANA Database Explorer or from Business Application Studio.

**Open Database Explorer from Business Application Studio:**

1.  Go to SAP HANA Project Explorer.

2.  Select the database connection.

3.  Choose *Open HDI Container*.

    You are taken to the Database Explorer.


**From SAP HANA Database Explorer:**

1.  Expand the container node.

2.  From the list of object types, choose *Column Views*.

3.  To display the contents of the calculation view, from the context menu, choose *Open Data* from the Catalog Browser.


**From Business Application Studio:**

1.  Select the node below *Semantics*.

2.  From the context menu, choose:


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
    

**Preview Output of Intermediate Nodes**

You can preview the data as it is processed at a specific node. This preview allows you to see the output data that is passed to the higher view node levels. To start an intermediate data preview, choose a data preview action from the context menu of the node.

**Related Information**  


[Data Analysis](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2023_2_QRC/en-US/42beb7bab4484130958ef62ee7b031aa.html "After you have modeled a calculation view, you can analyze its output.") :arrow_upper_right:

[Configuring Data Preview Behavior](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2023_2_QRC/en-US/92883c2b13c74649b183590c4b5744ae.html "You can configure different preview options.") :arrow_upper_right:

[Create Calculation Views](create-calculation-views-5aeb56c.md "Use a graphical editor to create calculation views that depict complex business scenarios.")

