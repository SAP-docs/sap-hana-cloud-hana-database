<!-- loiof0557bf56f45441fb3a324a7cda07e30 -->

# Configure a Custom Set of Build Plug-in Libraries Available to an SAP HDI Container

Maintain a custom set of plug-in libraries available in an SAP HDI container.



<a name="loiof0557bf56f45441fb3a324a7cda07e30__context_zgt_z32_l1b"/>

## Context

In SAP HANA Deployment Infrastructure \(HDI\), HDI container administrators can configure a custom set of commonly used HDI plug-in libraries for any container for which they are responsible. It is possible to define the full set of libraries, or incrementally add or remove certain libraries to the currently configured set.



<a name="loiof0557bf56f45441fb3a324a7cda07e30__steps_hnw_j32_l1b"/>

## Procedure

1.  In an SQL console, connect to the database as an administrator of the target HDI container, for example, “C”.

2.  Open the SQL editor for this database.

3.  Define a custom list of plug-in libraries available in the specified target container.

    Insert the following SQL statement into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #LIBRARY_CONFIGURATION LIKE _SYS_DI.TT_LIBRARY_CONFIGURATION;
    > INSERT INTO #LIBRARY_CONFIGURATION ( ACTION, LIBRARY_NAME ) VALUES ( 'ADD', 'com.sap.hana.di.calculationview' );
    > INSERT INTO #LIBRARY_CONFIGURATION ( ACTION, LIBRARY_NAME ) VALUES ( 'ADD', 'com.sap.hana.di.cds' );
    > INSERT INTO #LIBRARY_CONFIGURATION ( ACTION, LIBRARY_NAME ) VALUES ( 'ADD', 'com.sap.hana.di.synonym' );
    > INSERT INTO #LIBRARY_CONFIGURATION ( ACTION, LIBRARY_NAME ) VALUES ( 'REMOVE', 'com.sap.hana.di.view' );
    > CALL C#DI.CONFIGURE_LIBRARIES(#LIBRARY_CONFIGURATION, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #LIBRARY_CONFIGURATION;
    > 
    > ```

    1.  Replace the name of the container “C” in the `CALL` statement with the name of your container.

    2.  Adjust the set of libraries to be added or removed in the `INSERT` statements as needed. This example adds three libraries and removes one.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(**Optional**\) Confirm that the custom set of libraries has been configured successfully by listing all currently configured build plug-in libraries available in the container.

6.  \(**Optional**\) Customize the configuration of the build plug-in library if necessary.

    The behavior of the build plug-ins library configuration can be modified by supplying custom parameters in the call to `CONFIGURE_LIBRARIES` instead of `_SYS_DI.T_NO_PARAMETERS`.

    For example, to remove a build plug-in library and **undeploy** all files `('undeploy', 'true')` corresponding to that library, use the following SQL code:

    > ### Note:  
    > The default value for the `undeploy` parameter is `'false'`

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PARAMETERS LIKE _SYS_DI.TT_PARAMETERS;
    > INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('undeploy', 'true');
    > CREATE LOCAL TEMPORARY COLUMN TABLE #LIBRARY_CONFIGURATION LIKE _SYS_DI.TT_LIBRARY_CONFIGURATION;
    > INSERT INTO #LIBRARY_CONFIGURATION ( ACTION, LIBRARY_NAME ) VALUES ( 'REMOVE', 'com.sap.hana.di.view' );
    > CALL C#DI.CONFIGURE_LIBRARIES(#LIBRARY_CONFIGURATION, #PARAMETERS, ?, ?, ?);
    > DROP TABLE #LIBRARY_CONFIGURATION;
    > DROP TABLE #PARAMETERS;
    > 
    > ```


**Related Information**  


[List All Currently Configured Build Plug-in Libraries Available to an SAP HDI Container](list-all-currently-configured-build-plug-in-li-ddb04a9.md "Display a list of all the build plug-in libraries available for use in an SAP HDI container.")

[Configure the Default Build Plug-in Libraries Available to an SAP HDI Container](configure-the-default-build-plug-in-libraries-016e9af.md "Maintain the set of plug-in libraries available by default in an SAP HDI container.")

[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

