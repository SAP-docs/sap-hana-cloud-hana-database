<!-- loiod75182444361461992bcd331f3a16695 -->

# GRANT\_CONTAINER\_SCHEMA\_PRIVILEGES

Grant access privileges to a database object consumer for the entire container schema where the database objects are located.



Users that would like to consume objects deployed to an HDI container need to be granted the appropriate privileges. The privileges can be granted to specific objects in the schema \(for example, C\) by use of a role that has been deployed to the target container \(see *GRANT\_CONTAINER\_SCHEMA\_ROLES*\), or by granting privileges for the entire schema \(*GRANT\_CONTAINER\_SCHEMA\_PRIVILEGES*\). Privileges granted by the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES` can be revoked with the procedure `REVOKE_CONTAINER_SCHEMA_PRIVILEGES`.



<a name="loiod75182444361461992bcd331f3a16695__section_kxz_1ck_dfb"/>

## Signature

> ### Sample Code:  
> ```sql
> GRANT_CONTAINER_SCHEMA_PRIVILEGES
>  (
>   IN  PRIVILEGES  _SYS_DI.TT_SCHEMA_PRIVILEGES,
>   IN  PARAMETERS  _SYS_DI.TT_PARAMETERS,
>   OUT RETURN_CODE INT,
>   OUT REQUEST_ID  BIGINT,
>   OUT MESSAGES    _SYS_DI.TT_MESSAGES 
>  )
> ```



<a name="loiod75182444361461992bcd331f3a16695__section_jpl_3ck_dfb"/>

## Parameters

The following parameters can be used with `IN` and `OUT` parameters in the `GRANT_CONTAINER_SCHEMA_PRIVILEGES` command:



### PRIVILEGES \[IN\]

The list of privileges for the container schema which you want to grant to a principal.

**\_SYS\_DI.TT\_SCHEMA\_PRIVILEGES**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

PRIVILEGE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Name of the schema privilege to be granted. The following list shows the permitted privileges for HDI container schemas:

-   CREATE ANY

-   CREATE TEMPORARY TABLE

-   EXECUTE

-   SELECT CDS METADATA

-   SELECT METADATA

-   SELECT

-   INSERT

-   UPDATE

-   DELETE

-   DEBUG

-   UNMASKED




</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The schema name of the principal. This is needed, for example, if the principal is a schema-local role.

</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the principal

</td>
</tr>
</table>



### PARAMETERS \[IN\]

Additional parameters can be used to control various aspects of the procedure execution. If no parameters are needed, the empty predefined parameters table `_SYS_DI.T_NO_PARAMETERS` can be used.

**\_SYS\_DI.TT\_PARAMETERS**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

KEY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The key name of the parameter

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The value assigned to the parameter

</td>
</tr>
</table>

The following additional parameters are available:

-   `container_lock_wait_timeout`

-   `trace_context`

-   `trace_level.<trace topic>`

-   `message_severity`




### RETURN\_CODE \[OUT\]

The return code indicates if the procedure executed successfully. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### REQUEST\_ID \[OUT\]

A unique ID is generated for each HDI container API call. For more details about which IDs are generated for API calls, see *The SQL API for SAP HDI* in *Related Information*.



### MESSAGES \[OUT\]

A table is used to display messages that contain information logged during \(and about\) the execution of the procedure. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



<a name="loiod75182444361461992bcd331f3a16695__section_zwq_m2k_dfb"/>

## Examples

To grant access privileges for the container schema \("C" in this example\) to another user, for example, `NEW_CONTAINER_CONSUMER`, use a command like the one shown in the following example:

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_SCHEMA_PRIVILEGES;
> INSERT INTO #PRIVILEGES(PRIVILEGE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME) VALUES ('SELECT', '', 'NEW_CONTAINER_CONSUMER');
> CALL <container name>#DI.GRANT_CONTAINER_SCHEMA_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PRIVILEGES; 
> ```

To grant privileges on the container schema "C" to a role \(for example, `ROLE_IN_CONTAINER_D`\) in another container or schema \("D" in this example\), use a command like the one shown in the following example:

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_SCHEMA_PRIVILEGES;
> INSERT INTO #PRIVILEGES(PRIVILEGE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME) VALUES ('INSERT', 'D', 'ROLE_IN_CONTAINER_D');
> CALL <container name>#DI.GRANT_CONTAINER_SCHEMA_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PRIVILEGES; 
> ```

**Related Information**  


[REVOKE\_CONTAINER\_SCHEMA\_PRIVILEGES](revoke-container-schema-privileges-c9c9455.md "Revoke access privileges from a database object consumer for the entire container schema where the database objects are located.")

[GRANT\_CONTAINER\_SCHEMA\_ROLES](grant-container-schema-roles-2429050.md "Enable access to objects in a container schema by means of a role already deployed to the container schema.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

[Available SAP HDI Parameters](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/e2d3e543067e4f3282bf6dbf880c6b2d.html?version=2023_3_QRC#available-sap-hdi-parameters)

