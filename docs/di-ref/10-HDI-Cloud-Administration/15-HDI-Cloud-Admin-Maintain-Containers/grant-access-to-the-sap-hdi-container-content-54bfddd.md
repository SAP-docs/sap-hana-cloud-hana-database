<!-- loio54bfddddfa554004950de3a4ca0c2a7c -->

# Grant Access to the SAP HDI Container Content-Development API

Enable access to the content-development application programming interface \(API\) for an SAP HDI container.



<a name="loio54bfddddfa554004950de3a4ca0c2a7c__context_ovn_h3d_l1b"/>

## Context

In SAP HANA Deployment Infrastructure \(HDI\), the content-development API in a container's `#DI` schema \(for example, schema `C#DI` in container “C”\) is intended for use by developers of HDI database artifacts. Developers use the container content-development API to write design-time artifacts to the container; the design-time artifacts are then used to generate database objects in the container's schema \(for example, schema `C` in container “C”\). A container administrator must first grant the necessary privileges to the developer before the API can be used, as described below.

> ### Note:  
> The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_USER_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the scope of the privileges granted by not using this default table and explicitly specifying the desired set of privileges instead.



<a name="loio54bfddddfa554004950de3a4ca0c2a7c__steps_pvn_h3d_l1b"/>

## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Grant access to the HDI container content-development API.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_CONTENT_DEVELOPER', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_USER_PRIVILEGES;
    > CALL C#DI.GRANT_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES;
    > 
    > ```

    1.  Adjust the name of the new content-development user “`NEW_CONTAINER_CONTENT_DEVELOPER`” in the `INSERT` statement in line 2 to reflect the name of the user to whom the API privileges should be granted.

    2.  Adjust the name of the container's API schema `C#DI` in the `CALL` statement to suit your needs.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_CONTENT_DEVELOPER` user is now able to call the HDI container content-development API in the containers API schema \(for example, `C#DI` in container “C”\).


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Revoke Access to the SAP HDI Container Content-Development API](revoke-access-to-the-sap-hdi-container-content-32dbec7.md "Disable access to the content-development application programming interface (API) for an SAP HDI container.")

