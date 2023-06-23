<!-- loio7c989fa6770d46109d37e8ad2a54447a -->

# Configure SAP HDI Parameters

The SAP HANA Deployment Infrastructure \(HDI\) administrator can configure some general aspects of the HDI with parameters, for example, how long an HDI operation waits for a locking conflict to clear or the default behavior of HDI containers.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Configure the required configuration parameters by executing the following SQL statement:

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS;
    INSERT INTO #CONFIG_PARAMETERS (KEY, VALUE) VALUES ('make.default_max_parallel_jobs', '<value>');
    -- insert more parameters as required
    CALL _SYS_DI.CONFIGURE_DI_PARAMETERS(#CONFIG_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    DROP TABLE #CONFIG_PARAMETERS;
    
    ```

    For a description of all available parameters, see *SAP HANA DI Configuration Parameters*.

3.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

4.  Verify that the configuration parameters have been set correctly in the `diserver.ini` configuration file.


**Related Information**  


[SAP HDI Configuration Parameters](sap-hdi-configuration-parameters-1d9582a.md "Configuration parameters are used to configure the behavior of SAP HANA Deployment Infrastructure (HDI).")

