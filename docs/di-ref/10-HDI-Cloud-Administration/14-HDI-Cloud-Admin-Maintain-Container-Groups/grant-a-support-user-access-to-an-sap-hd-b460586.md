<!-- loiob460586c9fe14618a69f4b3dec152659 -->

# Grant a Support User Access to an SAP HDI Container

Provide members of the support teams with temporary access to an SAP HDI container.



## Context

In the event of container-related problems in SAP HANA Deployment Infrastructure \(HDI\), it might be necessary for a support user to access HDI-internal objects in a container API schema, for example, `C#DI` for the container “C”. These privileges must be temporarily granted to an explicit support user and then revoked when the support task is completed.

> ### Caution:  
> The use of this function is only recommended in exceptional circumstances; it allows the support user to access all the data in the container, some of which could be private or confidential. Use of this function could also compromise the integrity of the container resulting in an unusable container or data loss. Enabling a support user to access a container raises a security alert to the database administrator.



## Procedure

1.  In an SQL console, connect to the database with the administrator of the HDI container group G.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI#G.GRANT_CONTAINER_SUPPORT_PRIVILEGE( 'C', 'SELECT', 'CONTAINER_SUPPORT_USER', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > ```

4.  Adjust the schema name of the container group G's API schema `_SYS_DI#G`.

5.  Adjust the name of the container “C”.

6.  Adjust the privilege as needed.

    Possible values are `SELECT`, `UPDATE`, `INSERT`, and `DELETE`.

7.  Adjust the name of the user `CONTAINER_SUPPORT_USER`.

8.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

9.  \(Optional\) Confirm that the `CONTAINER_SUPPORT_USER` user can now access objects in the container C's API schema `C#DI` per the given privileges.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Revoke Access to an SAP HDI Container from a Support User](revoke-access-to-an-sap-hdi-container-fr-5316825.md "Revoke any privileges granted to members of the support teams for temporary access to SAP HDI containers.")

