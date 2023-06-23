<!-- loiod87e9a9aa6d24a609ab95d6fa87508fd -->

# Configure SAP HDI Container Parameters

Maintain the parameters used to configure an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), the HDI container administrator can use configuration parameters to maintain some of the more general aspects of an HDI container. Container-specific configuration parameters are used to control the behavior of a single container, for example, they can be used to specify the time a container operation waits for a locking conflict to clear, or the maximum number of parallel jobs to be spawned during a make operation.

> ### Tip:  
> For more information about HDI configuration parameters, see *Related Information*.

To configure container-specific parameters, perform the following steps:



## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Define and set the parameters required for the configuration of the target HDI container.

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    > INSERT INTO #CONFIG_PARAMETERS (KEY, VALUE) VALUES ('make.max_parallel_jobs', '8');
    > CALL C#DI.CONFIGURE_CONTAINER_PARAMETERS(#CONFIG_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #CONFIG_PARAMETERS; 
    > ```

    1.  Add more parameters and values as required.

        > ### Tip:  
        > A new `INSERT` statement is required for each new parameter.

        ```sql
        INSERT INTO #CONFIG_PARAMETERS (KEY, VALUE) VALUES ('make.max_parallel_jobs', '8');
        INSERT INTO #CONFIG_PARAMETERS (KEY, VALUE) VALUES ('connection.transaction_lock_wait_timeout', '1,000');
        INSERT INTO #CONFIG_PARAMETERS (KEY, VALUE) VALUES ('messages.days_to_keep', '30');
        ...
        ```

    2.  Adjust the schema name of the container \(“C”\) in the `CALL` statement.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.


**Related Information**  


[SAP HDI Parameters](../13-HDI-Cloud-Admin-Maintain-HDI/sap-hdi-parameters-e2d3e54.md "An overview of the parameters available for the SAP HANA Deployment Infrastructure (HDI) and the corresponding build plug-ins.")

[SAP HDI Configuration Parameters](../13-HDI-Cloud-Admin-Maintain-HDI/sap-hdi-configuration-parameters-1d9582a.md "Configuration parameters are used to configure the behavior of SAP HANA Deployment Infrastructure (HDI).")

