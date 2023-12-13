<!-- loiofe51ebe5102c4991813a04b68843515f -->

# Drop an SAP HDI Container

In SAP HANA Deployment Infrastructure \(HDI\), the HDI container-group administrator can drop a container.



## Context

HDI container-group administrators can drop HDI containers from any empty or non-empty HDI container group for which they are responsible.



## Procedure

1.  In an SQL console, connect to the database as administrator of the target HDI container group \(for example, "G"\).

2.  Open the SQL editor for this database.

3.  Drop the container.

    Insert the following SQL code into the SQL console:

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI#G.DROP_CONTAINER('C', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

    To drop an HDI container that is not empty, use the following code:

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #DROP_CONTAINER_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS;
    INSERT INTO #DROP_CONTAINER_PARAMETERS ( KEY, VALUE ) VALUES ( 'ignore_work', 'true' );
    INSERT INTO #DROP_CONTAINER_PARAMETERS ( KEY, VALUE ) VALUES ( 'ignore_deployed', 'true' );
    CALL _SYS_DI#G.DROP_CONTAINER('C', #DROP_CONTAINER_PARAMETERS, ?, ?, ?);
    DROP TABLE #DROP_CONTAINER_PARAMETERS; 
    ```

4.  Adjust the name of the container group “G” and the name of the new container “C” in the `CALL` statement to suit the names of your container group and container respectively.

    The following example uses the group name "`myContainerGroup`" and container name "`myContainer`":

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI#<myContainerGroup>.DROP_CONTAINER('<myContainer>', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

5.  Execute the SQL code.

    Check that the code completes successfully with the HDI return code 0.

6.  \(Optional\) Confirm that the container no longer exists by checking that a corresponding entry has been removed from the list displayed in the container group schema's `_SYS_DI#G.M_CONTAINERS` view.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Create an SAP HDI Container](create-an-sap-hdi-container-d915699.md "In SAP HANA Deployment Infrastructure (HDI), the HDI container-group administrator can create a new container.")

[HDI Container Views](../../20-HDI-Cloud-Content-Development/hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

