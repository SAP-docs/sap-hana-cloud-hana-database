<!-- loioe081abacfa1e42ada7efbdcd80339caf -->

# Revoke Access to an SAP HDI Container's Schema

Revoke access to the schema of an SAP HDI container or specific objects in the target schema.



<a name="loioe081abacfa1e42ada7efbdcd80339caf__context_ovn_h3d_l1b"/>

## Context

In SAP HANA Deployment Infrastructure \(HDI\), users that need to consume objects deployed in a container \(for example, *<container\_name\>*\) must be granted the appropriate privileges to access the target container's schema \(for example, <code><i class="varname">&lt;container_name&gt;</i>#DI</code>\). The privileges for the entire schema can be revoked with the `REVOKE_CONTAINER_SCHEMA_PRIVILEGES` API.

To revoke privileges for the entire container schema where the database objects are located from a database object consumer `NEW_CONTAINER_CONSUMER` perform the following steps:



<a name="loioe081abacfa1e42ada7efbdcd80339caf__steps_pvn_h3d_l1b"/>

## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, *<container\_name\>*\).

2.  Open the SQL editor for this database.

3.  Revoke access to the HDI container's schema.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_SCHEMA_PRIVILEGES;
    > INSERT INTO #PRIVILEGES ( PRIVILEGE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME ) VALUES ( 'SELECT', '', '<NEW_CONTAINER_CONSUMER>' );
    > CALL <container_name>#DI.REVOKE_CONTAINER_SCHEMA_PRIVILEGES( #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES;
    > 
    > ```

    1.  In the `INSERT` statement in line 2, replace the name of the consumer user *<NEW\_CONTAINER\_CONSUMER\>* with the name of the user whose container-access privileges must be revoked.

    2.  In the `CALL` statement, replace *<container\_name\>* in the name of the container's API schema \(<code><i class="varname">&lt;container_name&gt;</i>#DI</code>\) with the name of your container.


4.  Run the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the *<NEW\_CONTAINER\_CONSUMER\>* can no longer access the database objects in *<container\_name\>*'s schema.


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Grant Access to an SAP HDI Container's Schema](grant-access-to-an-sap-hdi-container-s-schema-14ccad2.md "Enable access to the schema of an SAP HDI container of individual objects in the target schema.")

[SAP HDI Container Schemas](sap-hdi-container-schemas-71ed23c.md "An SAP HANA Deployment Infrastructure (HDI) container makes use of multiple schemas; each of the different schemas serves different aims and tasks.")

