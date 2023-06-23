<!-- loio14ccad20b2b64190b269a488e0f44cbc -->

# Grant Access to an SAP HDI Container's Schema

Enable access to the schema of an SAP HDI container of individual objects in the target schema.



<a name="loio14ccad20b2b64190b269a488e0f44cbc__context_ovn_h3d_l1b"/>

## Context

In SAP HANA Deployment Infrastructure \(HDI\), users that would like to consume objects deployed to an HDI container need to be granted the appropriate privileges. The privileges can be granted to specific objects in the schema \(for example, `C`\) by use of a role that has been deployed to the target container, for example, “C”, or by granting privileges for the entire schema.

To grant access privileges for the entire container schema where the database objects are located to a database object consumer `NEW_CONTAINER_CONSUMER`, perform the following steps:



<a name="loio14ccad20b2b64190b269a488e0f44cbc__steps_pvn_h3d_l1b"/>

## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Grant access to the HDI container's schema.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_SCHEMA_PRIVILEGES; 
    > INSERT INTO #PRIVILEGES ( PRIVILEGE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME ) VALUES ( 'SELECT', '', 'NEW_CONTAINER_CONSUMER' );
    > CALL C#DI.GRANT_CONTAINER_SCHEMA_PRIVILEGES( #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES;
    > ```

    1.  Adjust the name of the consumer user “`NEW_CONTAINER_CONSUMER`” in the `INSERT` statement in line 2 to reflect the name of the user who requires access to the container.

    2.  Adjust the name of the container's API schema \(`C#DI`\) in the `CALL` statement to suit your needs.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_CONSUMER` can now access the database objects in the container's schema.


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Revoke Access to an SAP HDI Container's Schema](revoke-access-to-an-sap-hdi-container-s-schema-e081aba.md "Revoke access to the schema of an SAP HDI container or specific objects in the target schema.")

[SAP HDI Container Schemas](sap-hdi-container-schemas-71ed23c.md "An SAP HANA Deployment Infrastructure (HDI) container makes use of multiple schemas; each of the different schemas serves different aims and tasks.")

