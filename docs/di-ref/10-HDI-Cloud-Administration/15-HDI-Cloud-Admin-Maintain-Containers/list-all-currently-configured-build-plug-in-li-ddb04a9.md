<!-- loioddb04a9bbbe645f7bcfecf38c599e279 -->

# List All Currently Configured Build Plug-in Libraries Available to an SAP HDI Container

Display a list of all the build plug-in libraries available for use in an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), administrators of an HDI container \(for example, container *<container\_name\>*\) can view all currently configured HDI build plug-in libraries and their versions for any container where they have the container-administration permissions, as described in the following procedure:



## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container, for example, *<container\_name\>*.

2.  Open the SQL editor for this database.

3.  Display a list of all currently available plug-ins in the specified container.

    Insert the following SQL statement into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CALL <container_name>#DI.LIST_CONFIGURED_LIBRARIES(_SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?); 
    > ```

    1.  Replace *<container\_name\>* in the `CALL` statement with the name of your container.


4.  Run the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  A result set with the requested plug-in information is returned.

    The following example shows an excerpt from the result set returned:

    > ### Output Code:  
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


**Related Information**  


[Configure the Default Build Plug-in Libraries Available to an SAP HDI Container](configure-the-default-build-plug-in-libraries-016e9af.md "Maintain the set of plug-in libraries available by default in an SAP HDI container.")

[Configure a Custom Set of Build Plug-in Libraries Available to an SAP HDI Container](configure-a-custom-set-of-build-plug-in-librar-f0557bf.md "Maintain a custom set of plug-in libraries available in an SAP HDI container.")

[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

