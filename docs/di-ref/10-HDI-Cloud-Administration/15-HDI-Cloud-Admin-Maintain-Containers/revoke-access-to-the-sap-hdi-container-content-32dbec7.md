<!-- loio32dbec7ee46445ce9611066a6a7642e3 -->

# Revoke Access to the SAP HDI Container Content-Development API

Disable access to the content-development application programming interface \(API\) for an SAP HDI container.



<a name="loio32dbec7ee46445ce9611066a6a7642e3__context_ovn_h3d_l1b"/>

## Context

In SAP HANA Deployment Infrastructure \(HDI\), the content-development API in an HDI container's schema \(for example, schema `C#DI` in container “C”\) is intended for use by developers of HDI database artifacts. Developers use the container content-development API to write design-time artifacts to the container; the design-time artifacts are then used to generate database objects in the container's schema \(for example, schema `C#DI` in container “C”. A container administrator can revoke the privileges that enable access to the container content-development API at any time, as described below.

> ### Note:  
> The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_USER_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the scope of the privileges granted by not using this default table and explicitly specifying the desired set of privileges instead.



<a name="loio32dbec7ee46445ce9611066a6a7642e3__steps_pvn_h3d_l1b"/>

## Procedure

1.  In an SQL console, connect to the database as an administrator of the HDI container whose development API you want to disable \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Revoke access to the HDI container content-development API.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_CONTENT_DEVELOPER', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_USER_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%');
    > CALL C#DI.REVOKE_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  In the `INSERT` statement in line 2, adjust the name of the new content-development user “`NEW_CONTAINER_CONTENT_DEVELOPER`” to reflect the name of the user from whom the API privileges should be revoked.

    2.  In the `CALL` statement in line 3, adjust the name of the container's API schema `C#DI` to suit your needs.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_CONTENT_DEVELOPER` user is no longer able to call the HDI container content-development API in the containers API schema \(for example, `C#DI` in container “C”\).


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Grant Access to the SAP HDI Container Content-Development API](grant-access-to-the-sap-hdi-container-content-54bfddd.md "Enable access to the content-development application programming interface (API) for an SAP HDI container.")

