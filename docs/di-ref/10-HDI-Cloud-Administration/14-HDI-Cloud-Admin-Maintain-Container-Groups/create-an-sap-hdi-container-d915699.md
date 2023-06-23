<!-- loiod9156997277f4af9a7837ea1efce82ec -->

# Create an SAP HDI Container

In SAP HANA Deployment Infrastructure \(HDI\), the HDI container-group administrator can create a new container.



## Context

HDI container-group administrators can create HDI containers in any HDI container group for which they are responsible.



<a name="loiod9156997277f4af9a7837ea1efce82ec__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database as administrator of the target HDI container group \(for example, "G"\).

2.  Open the SQL editor for this database.

3.  Create the container.

    Insert the following SQL code into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI#G.CREATE_CONTAINER('C', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

4.  Adjust the name of the container group “G” and the name of the new container “C” to suit the names of your container group and container respectively.

5.  Execute the SQL code.

    Check that the code completes successfully with the HDI return code 0.

6.  \(Optional\) Confirm that the container exists by checking that a corresponding new entry has been added to the container group schema's `_SYS_DI#G.M_CONTAINERS` view.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Drop an SAP HDI Container](drop-an-sap-hdi-container-fe51ebe.md "In SAP HANA Deployment Infrastructure (HDI), the HDI container-group administrator can drop a container.")

