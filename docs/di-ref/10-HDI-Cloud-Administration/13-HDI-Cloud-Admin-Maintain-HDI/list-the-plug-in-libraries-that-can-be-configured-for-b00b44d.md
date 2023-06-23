<!-- loiob00b44d7881a46339e3ed6a25df99b67 -->

# List The Plug-in Libraries That Can Be Configured for an SAP HDI Container

You can find out which SAP HANA Deployment Infrastructure \(HDI\) plug-in libraries and versions are available in the database and can be configured for use in an HDI container.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Display a list of plug-in libraries available in the HDI container.

    Run the following SQL statement

    ```sql
    CALL _SYS_DI.LIST_LIBRARIES(_SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?);
    ```

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

3.  Examine the result set returned by SQL.

    The following example shows an excerpt of a typical result set for this request:

    > ### Output Code:  
    > Excerpt of result set
    > 
    > ```
    > LIBRARY_NAME;LIBRARY_VERSION;PLUGIN_ID;PLUGIN_VERSION
    > com.sap.hana.di.afllangprocedure;0.0;com.sap.hana.di.afllangprocedure;4.0.0.0
    > com.sap.hana.di.analyticprivilege;0.0;com.sap.hana.di.analyticprivilege;4.0.0.0
    > com.sap.hana.di.calculationview;0.0;com.sap.hana.di.calculationview;4.0.0.0
    > com.sap.hana.di.cds;0.3;com.sap.hana.di.cds;4.0.0.0
    > com.sap.hana.di.constraint;0.0;com.sap.hana.di.constraint;4.0.0.0
    > com.sap.hana.di.copyonly;0.0;com.sap.hana.di.copyonly;4.0.0.0
    > com.sap.hana.di.dropcreatetable;0.0;com.sap.hana.di.dropcreatetable;4.0.0.0
    > com.sap.hana.di.flowgraph;0.0;com.sap.hana.di.flowgraph;4.0.0.0
    > 
    > ```


