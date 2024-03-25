<!-- loiobb47fc06c27841449017d055302a4074 -->

# Revoke a Role from the SAP HDI Container's Schema

Use a role to disable access to an SAP HDI container's schema objects.



<a name="loiobb47fc06c27841449017d055302a4074__context_jvz_ntd_l1b"/>

## Context

In SAP HANA Deployment Infrastructure \(HDI\), users who would like to consume objects deployed to an SAP HDI container \(for example, named *<container\_name\>*\) need to be granted the appropriate access privileges for the container's schema. The privileges for specific objects in the target schema \(for example, <code><i class="varname">&lt;container_name&gt;</i>#DI</code>\), granted by a role in the schema, can be revoked with the `REVOKE_CONTAINER_SCHEMA_ROLES` API:

To revoke a role and disable access privileges for specific objects in the container from a user, perform the following steps:



<a name="loiobb47fc06c27841449017d055302a4074__steps_kvz_ntd_l1b"/>

## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, *<container\_name\>*\).

2.  Open the SQL editor for this database.

3.  Grant the role to the target user.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #ROLES LIKE _SYS_DI.TT_SCHEMA_ROLES;
    > INSERT INTO #ROLES ( ROLE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME ) VALUES ( '<myrole'>, '', '<NEW_CONTAINER_CONSUMER>' );
    > CALL <container_name>#DI.REVOKE_CONTAINER_SCHEMA_ROLES(#ROLES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #ROLES; 
    > ```

    1.  In the `INSERT` statement in line 2, replace *<NEW\_CONTAINER\_CONSUMER\>* and the role "`myrole`" with the name of your container and role you want to revoke, respectively.

    2.  In the `CALL` statement in line 3, replace *<container\_name\>* in the container's API schema name \(<code><i class="varname">&lt;container_name&gt;</i>#DI</code>\) with the name of your container.


4.  Run the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the *<NEW\_CONTAINER\_CONSUMER\>* can no longer access the database objects specified by the role in *<container\_name\>*'s schema.


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Grant a User a Role from the SAP HDI Container's Schema](grant-a-user-a-role-from-the-sap-hdi-container-6574d8e.md "Use a role to enable access to an SAP HDI container's schema objects.")

