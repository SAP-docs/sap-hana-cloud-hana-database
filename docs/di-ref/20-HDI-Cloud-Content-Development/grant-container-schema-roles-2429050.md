<!-- loio2429050bf9f245a2b6fb47bbbed947f9 -->

# GRANT\_CONTAINER\_SCHEMA\_ROLES

Enable access to objects in a container schema by means of a role already deployed to the container schema.



Users who would like to consume objects deployed to a container need to be granted the appropriate privileges for the consumed objects. The access privileges can be granted to specific objects in the schema \(for example, `C#DI`\) by using a role that has been deployed to the container \(`GRANT_CONTAINER_SCHEMA_ROLES`\), or by granting privileges for the entire schema, for example, with the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES`.



<a name="loio2429050bf9f245a2b6fb47bbbed947f9__section_g3d_b3k_dfb"/>

## Signature

> ### Sample Code:  
> ```sql
> GRANT_CONTAINER_SCHEMA_ROLES
>  (
>   IN  PRIVILEGES  _SYS_DI.TT_SCHEMA_ROLES,
>   IN  PARAMETERS  _SYS_DI.TT_PARAMETERS,
>   OUT RETURN_CODE INT,
>   OUT REQUEST_ID  BIGINT,
>   OUT MESSAGES    _SYS_DI.TT_MESSAGES 
>  )
> ```



<a name="loio2429050bf9f245a2b6fb47bbbed947f9__section_fqy_23k_dfb"/>

## Parameters

The following parameters can be used with `IN` and `OUT` parameters in the `GRANT_CONTAINER_SCHEMA_ROLES` command:



### PRIVILEGES \[IN\]

The list of roles from the container schema which you want to grant to a principal.

**\_SYS\_DI.TT\_SCHEMA\_ROLES**


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

ROLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Name of the role to be granted.

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


> ### Tip:  
> For more information about all available SAP HANA HDI parameters, see *Available SAP HDI Parameters* in *Related Information* below.



### RETURN\_CODE \[OUT\]

The return code indicates if the procedure executed successfully. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### REQUEST\_ID \[OUT\]

A unique ID is generated for each HDI container API call. For more details about which IDs are generated for API calls, see *The SQL API for SAP HDI* in *Related Information*.



### MESSAGES \[OUT\]

A table is used to display messages that contain information logged during \(and about\) the execution of the procedure. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



<a name="loio2429050bf9f245a2b6fb47bbbed947f9__section_vvy_43k_dfb"/>

## Examples

To grant a role from the container schema \("C" in this example\) to another user, for example, `NEW_CONTAINER_CONSUMER`, use a command like the one shown in the following example:

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #ROLES LIKE _SYS_DI.TT_SCHEMA_ROLES;
> INSERT INTO #ROLES(ROLE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME) VALUES ('myrole', '', 'NEW_CONTAINER_CONSUMER');
> CALL C#DI.GRANT_CONTAINER_SCHEMA_ROLES(#ROLES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #ROLES; 
> ```

To grant a role from the container schema "C" to another role \(for example, `ROLE_IN_CONTAINER_D`\) in another container or schema \("D" in this example\), use a command like the one shown in the following example:

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #ROLES LIKE _SYS_DI.TT_SCHEMA_ROLES;
> INSERT INTO #ROLES(ROLE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME) VALUES ('myrole', 'D', 'ROLE_IN_CONTAINER_D');
> CALL C#DI.GRANT_CONTAINER_SCHEMA_ROLES(#ROLES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #ROLES; 
> ```

**Related Information**  


[GRANT\_CONTAINER\_SCHEMA\_PRIVILEGES](grant-container-schema-privileges-d751824.md "Grant access privileges to a database object consumer for the entire container schema where the database objects are located.")

[REVOKE\_CONTAINER\_SCHEMA\_ROLES](revoke-container-schema-roles-83541ed.md "Disable access to objects in a container schema by means of a role from the container schema.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

[Available SAP HDI Parameters](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/e2d3e543067e4f3282bf6dbf880c6b2d.html?version=2023_3_QRC#available-sap-hdi-parameters)

