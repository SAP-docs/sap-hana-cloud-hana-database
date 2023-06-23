<!-- loio625d7733c30b4666b4a522d7fa68a550 -->

# Roles \(.hdbrole and .hdbroleconfig\)

Transform a design-time role resource \(`.hdbrole`\) into a run-time role object.



The role plug-in transforms a design-time role resource, a file with the `.hdbrole` extension, into a run-time role object. The format of the `.hdbrole` file must comply with the JSON syntax, and the file content specifies privileges and other roles to be included in the role to be activated.



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_p5g_jg1_1hb"/>

## Example Artifact Code

The following code shows a simple example of a role definition for HDI.

> ### Tip:  
> The following code sample is interactive; click the property you are interested in learning about to display more detailed information about how to configure and use it.

> ### Code Syntax:  
> `/src/myDesignTimeRole.hdbrole`
> 
> ```
> { 
>   "role":{ 
>     "pattern_escape_character": "\",
>     "name":"RoleX", 
>     "global_roles":[ 
>       "GLOBAL_ROLE_1", 
>       "GLOBAL_ROLE_2" 
>     ], 
>     "schema_roles":[ 
>       { 
>         "schema_reference":"RoleSchemaRef1", 
>         "names": ["RoleA", "RoleB"] 
>       }, 
>       { 
>         "schema_reference":"RoleSchemaRef2", 
>         "names": ["RoleB", "RoleC"] 
>       },
>       { 
>         "schema_reference":"LogicalSchemaRef1", 
>         "names": ["RoleD", "RoleE"] 
>       }  
>     ], 
>     "system_privileges":[ 
>       "BACKUP ADMIN", 
>       "USER ADMIN" 
>     ], 
>     "schema_privileges":[ 
>       { 
>         "reference":"Ref1", 
>         "privileges":[ "SELECT" ], 
>         "privileges_with_grant_option":[ "UPDATE" ] 
>       } 
>     ], 
>     "object_privileges":[ 
>       { 
>         "name":"Table1", 
>         "type":"TABLE", 
>         "privileges":[ "SELECT" ], 
>         "privileges_with_grant_option":[ "UPDATE" ] 
>       },
>       {  
>         "name":"<wildcard_object_identifier>",
>         "type":"TABLE",
>         "privileges":[ "SELECT" ],
>         "pattern_mode": "include"
>       }
>     ],
>     
>     "global_object_privileges":[ 
>       { 
>         "name":"My_Usergroup", 
>         "type":"USERGROUP", 
>         "privileges":[ "OPERATOR" ], 
>         "privileges_with_grant_option":[ "OPERATOR" ],
>         "schema_reference":"SchemaRef1"
>       }
>     ],  
>     "schema_analytic_privileges":[ 
>       { 
>         "schema_reference":"APSchemaRef1", 
>         "privileges": ["AP1", "AP2"], 
>         "privileges_with_grant_option": ["AP4"] 
>       }, 
>       { 
>         "schema_reference":"APSchemaRef2", 
>         "privileges": ["AP1", "AP3"] 
>       },
>       { 
>         "schema_reference":"LogicalSchemaRef1", 
>         "names": ["RoleAP1", "RoleAP3"] 
>       }  
>     ] 
>   } 
> }
> ```



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_z4z_bxz_zgb"/>

## Mandatory Role Properties

The following table lists the properties that must be defined in a design-time role definition.

**Mandatory Design-Time Role-Definition Properties**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [`"role"`](roles-hdbrole-and-hdbroleconfig-625d773.md#loio625d7733c30b4666b4a522d7fa68a550__section_xqy_kpk_bhb) 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The root of the JSON data structure and an object with a single key role



</td>
</tr>
<tr>
<td valign="top">

 [`"name"`](roles-hdbrole-and-hdbroleconfig-625d773.md#loio625d7733c30b4666b4a522d7fa68a550__section_qpz_xwz_zgb) 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The name of the role. The name is used as the name of the run-time role created in the database. Each role definition must have a valid name, which is a non-empty string that contains only permitted characters.



</td>
</tr>
</table>



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_xqy_kpk_bhb"/>

## role

The role object is mandatory; it is the root of the JSON data structure and an object with a single key role.

```json
{
  "role":{ 
  ... 
  }
} 
```



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_ik4_jsk_bhb"/>

## pattern\_escape\_character

the "`pattern_escape_character`" property is optional; it is only required if you want to change the default escape character \(%\) in search patterns for wild-card object privileges. The following example shows how to replace the default \(%\) character with the backslash character \(\\\) as the escape character in search patterns:

```json
"pattern_escape_character": "\",
```

The wildcard characters percentage \(%\) and underscore \( \_ \) can be used in the *<wilcard\_pattern\_expression\>*. The percentage sign \(%\) wildcard matches zero or more characters. The underscore \(\_\) wildcard matches exactly one character.

To match a percentage sign \(%\) or underscore \(\_\) with the `LIKE` predicate, an escape character must be placed in front of the wildcard character. Use <code>ESCAPE <i class="varname">&lt;escape_expression&gt;</i></code> to specify the escape character you are using, as illustrated in the following examples:

`LIKE 'data_%' ESCAPE '_'` matches the string `'data%'`

`LIKE 'data__%' ESCAPE '_'` \(two underscores, followed by a percent sign\) matches a string that starts with `'data_'`



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_qpz_xwz_zgb"/>

## name

Each role definition must have a valid name, which is a non-empty string. The value specified in `"name"` is used as the name of the run-time role created in the database.

```json
"name":"RoleX",
```

The following types of role name are allowed:

-   "`MyRole#`"

    Role names that end with the hash character \(\#\), for example, "`MyRole#`" can include "`with-grant-option`" privileges in the role along with references to other roles whose names also end with \#.

    > ### Note:  
    > A role name ending with \# can only be granted to the object owner of an HDI container \("<code><i class="varname">&lt;container&gt;</i>#OO</code>"\), for example, using the HDI APIs.

-   `MyRole`

    Role names that **do not**end with \#, for example, `MyRole`, can only include privileges **without** grant options and references to other roles whose names do not end with \#.




<a name="loio625d7733c30b4666b4a522d7fa68a550__section_upx_h4r_bhb"/>

## global\_roles

A role can include references to other global roles, which are roles that are created **without** a schema. A valid entry for a global role is any non-empty string, for example: "`GLOBAL_ROLE_1`" or `GLOBAL_ROLE_2`. Multiple roles are separated by a comma.

> ### Sample Code:  
> ```json
> "global_roles":[ 
>     "GLOBAL_ROLE_1", 
>     "GLOBAL_ROLE_2" 
> ], 
> ```



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_m4z_pwz_zgb"/>

## schema\_roles

A role can include references to other schema-local roles, which are roles created **with** a schema. A valid entry for schema-local roles consists of the following elements:

-   `"schema_reference"`

    A valid entry for a `"schema_reference"`, which is a unique identifier within the `.hdbrole` file and can be resolved to the name of a real schema or a logical schema by means of the role configuration file \(`.hdbroleconfig`\).

-   `"names"`

    A non-empty, comma-separated list with the names of the relevant roles created in the referenced schema. The `schema_reference` entry is optional. If omitted, the specified role names will refer to roles created in the schema of the object owner used in the deployment. The resolution of the schema references is based on configuration specified in a corresponding role-configuration file \(`.hdbroleconfig`\).


```json
"schema_roles":[ 
  { 
    "schema_reference":"RoleSchemaRef1", 
    "names": ["RoleA", "RoleB"] 
  } 
]
```



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_llw_kwz_zgb"/>

## system\_privileges

A role can include **system** privileges. The relevant system privileges are specified using a list. If the list is specified, it must not be empty and must contain valid system privileges.

```json
"system_privileges":[  
   "BACKUP ADMIN",
   "USER ADMIN"
 ],
```



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_r55_fwz_zgb"/>

## schema\_privileges

A role can include **schema** privileges. The relevant schema privileges can be specified using a list. If the list is specified, it must not be empty and must contain valid schema privileges.

```json
"schema_privileges":[  
   {  
     "reference":"Ref1",
     "privileges":[ "SELECT" ],
     "privileges_with_grant_option":[ "UPDATE" ]
   }
 ],
```

A valid entry for schema privileges consists of:

-   `"reference"`

    A unique identifier \(within the specified `.hdbrole` file\) that can be resolved to a real schema name in the corresponding role-configuration file \(`.hdbroleconfig`\)

-   `"privileges"`

    A non-empty, comma-separated list of schema privileges that are provided by the role **without** grant option

-   `"privileges_with_grant_option"`

    A non-empty, comma-separated list of schema privileges that are provided by the role **with** grant option.


> ### Note:  
> The <code>“reference”</code> entry is optional. If it is omitted, the specified privileges will refer to the schema of the object owner used in the deployment.

For any schema managed by HDI, only the following privileges can be specified: `ALTER, CREATE ANY, CREATE TEMPORARY TABLE, EXECUTE, SELECT, SELECT CDS METADATA, SELECT METADATA, ATTACH DEBUGGER, INSERT, UPDATE, DELETE, DEBUG, UNMASKED`.



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_dgc_xvz_zgb"/>

## object\_privileges

A role can include privileges on objects activated in the same container. The relevant object privileges can be specified using an <code>“object_privileges”</code> list. If the list of object privileges is specified, it must not be empty and must contain valid entries of object privileges.

```json
"object_privileges":[  
   {  
     "name":"Table1",
     "type":"TABLE",
     "privileges":[ "SELECT" ],
     "privileges_with_grant_option":[ "UPDATE" ]
    }
 ],
```

A valid entry for object privileges consists of the following elements:

-   `"name"`

    A valid string for the object name, or a synonym of the real object

-   `"type"`

    A valid string describing the object type, or the type of the real object in case of a synonym

-   `"privileges"`

    A non-empty, comma-separated list of all relevant and applicable privileges on the specified object, which are to be provided by the role **without** grant option

-   `"privileges_with_grant_option"`

    A non-empty, comma-separated list of relevant and applicable privileges, which are to be provided by the role **with** grant option.


The following object types are supported in the specification of object privileges:

-   Basic SQL types

    `INDEX`, `FUNCTION`, `PROCEDURE`, `SYNONYM`, `TABLE`, `TRIGGER`, `VIEW`


You can specify objects with wildcard object identifiers to “include” or “exclude” matching objects for a list of privileges. The wildcard object identifier is used in the same way as the SQL regular expression "`LIKE`".

```json
"object_privileges":[  
   {  
     "name":"<wildcard_object_identifier>",
     "type":"TABLE",
     "privileges":[ "SELECT" ],
     "pattern_mode": "include"
   },
   {  
     "name":"<wildcard_object_identifier>",
     "type":"TABLE",
     "privileges":[ "SELECT" ],
     "pattern_mode": "exclude"
    } 
],
```

-   <code><i class="varname">&lt;wildcard_object_identifier&gt;</i></code> is specified as a search pattern for object names in `"name"`, for example, `"TABLE%"` or `"TABLE%_HR"` and requires a `"pattern_mode"` section. The pattern mode must be set to one of the following values:

    -   `"include"`

        The search pattern is used to filter all matching objects at the point of deployment; the privileges defined in the `"privileges"` list are granted to the matched objects.

    -   `"exclude"`

        The search pattern is used to filter all matching objects at the point of deployment; the privileges defined in the `"privileges"` list are revoked from the matched objects.


-   The `"include"` and `"exclude"` pattern mode can be combined in one role several times with different privileges lists and object types.

-   <code><i class="varname">&lt;wildcard_object_identifier&gt;</i></code> can be used for objects of type `FUNCTION`, `PROCEDURE`, `SEQUENCE`, `TABLE`, and `VIEW`.

-   The wildcard characters percentage \(%\) and underscore \( \_ \) can be used in the *<wilcard\_pattern\_expression\>*. The percentage sign \(%\) wildcard matches zero or more characters. The underscore \(\_\) wildcard matches exactly one character.

    > ### Tip:  
    > The "`%`" character is also the character used to escape wildcard characters.


For any object managed by HDI, only the following privileges can be specified: `ALTER, CREATE ANY, CREATE TEMPORARY TABLE, EXECUTE, SELECT, SELECT CDS METADATA, SELECT METADATA, ATTACH DEBUGGER, INSERT, UPDATE, DELETE, DEBUG, UNMASKED`.



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_tjm_sp5_rqb"/>

## global\_object\_privileges

A role can include privileges on global objects that are located outside the HDI container in which the role is deployed. The relevant privileges can be specified using a privileges list. If the list is specified, it must not be empty and must contain valid global object privileges. To specify global objects that have a schema, a `"schema_reference"` is also required, as illustrated in the following example:

```json
"global_object_privileges":[
   {
     "name":"My_Usergroup", 
     "type":"USERGROUP", 
     "privileges":[ "OPERATOR" ], 
     "privileges_with_grant_option":[ "OPERATOR" ],
     "schema_reference":"SchemaRef1"
   }
 ],
```

A valid entry for **global** object privileges consists of the following elements:

-   `"name"`

    A valid string for the object name, or a synonym of the real object

-   `"type"`

    A valid string describing the object type, or the type of the real object in case of a synonym

-   `"privileges"`

    A non-empty, comma-separated list of all relevant and applicable privileges on the specified object, which are to be provided by the role **without** grant option

-   `"privileges_with_grant_option"`

    A non-empty, comma-separated list of relevant and applicable privileges, which are to be provided by the role **with** grant option.

-   `"schema_reference"`

    A valid entry for a `"schema_reference"`, which is a unique identifier within the `.hdbrole` file and can be resolved to the name of a real schema or a logical schema by means of the role configuration file \(`.hdbroleconfig`\).


The following object types are supported in the specification of object privileges:

-   Basic SQL types:

    `INDEX`, `FUNCTION`, `PROCEDURE`, `SYNONYM`, `TABLE`, `TRIGGER`, `VIEW`

-   Objects without a schema name:

    `USERGROUP`, `X509`, `JWT`




<a name="loio625d7733c30b4666b4a522d7fa68a550__section_slg_qvz_zgb"/>

## schema\_analytic\_privileges

A role can include analytic privileges \(also called structured privileges\) specified in a list. Only schema-local analytic privileges \(created with a schema\) are supported. If the list of structured privileges is specified, it must not be empty and must contain valid entries.

```json

"schema_analytic_privileges":[
   {
     "schema_reference":"APSchemaRef1",
     "privileges": ["AP1", "AP2"],
     "privileges_with_grant_option": ["AP4", "AP6"]
   }
 ],
```

A valid entry for schema-local analytic privileges consists of: the following elements:

-   `"schema_reference"`

    A string that uniquely identifies the schema within the `.hdbrole` file and can be resolved to a real schema name in the corresponding role-configuration file \(`.hdbroleconfig`\)

-   `"privileges"`

    A non-empty, comma-separated list of relevant analytic privileges created in the referenced schema. These privileges are provided by the role **without** grant option.

-   `"privileges_with_grant_option"`

    A non-empty, comma-separated list of relevant analytic privileges, which are to be provided by the role **with** grant option.


> ### Note:  
> The `schema_reference` entry is optional. If omitted, the specified privileges will refer to analytic privileges created in the schema of the object owner used in the deployment. The resolution of any schema reference is based on the configuration specified in a corresponding role-configuration file \(`.hdbroleconfig`\).



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_c34_mvz_zgb"/>

## Role Configuration File

If required, a role definition can be complemented by a configuration, which must be specified in a role-configuration \(`.hdbroleconfig`\) file, whose contents must comply with the JSON format. The role-configuration file is optional and contains the resolution of the schema reference for schema privileges, roles, and analytic privileges contained in the role, as illustrated in the following example:

> ### Code Syntax:  
> `/src/myDesignTimeRole.hdbroleconfig`
> 
> ```json
> { 
>   "RoleX":{ 
>     "Ref1":{ 
>       "schema":"Schema1" 
>     }, 
>     "RoleSchemaRef1":{ 
>       "schema":"Schema2" 
>     }, 
>     "APSchemaRef1":{ 
>       "schema":"Schema3" 
>     }, 
>     "LogicalSchemaRef1":{ 
>       "logical_schema":"LogicalSchema1" 
>     } 
>   } 
> }
> ```

In the role-configuration file, the root object is identified by the name of the role, `"RoleX"` in this example. It contains a list of mappings. Each mapping is in turn identified by the reference name, for example, `"Ref1"`, `"Ref2"`. It is possible to specify references of type `"schema"` and `"logical_schema"`.

> ### Note:  
> The `"logical_schema"` field has a deployment dependency to a logical schema definition, which contains the schema to be used. For more information about defining a logical schema in a `.hdblogicalschema` file, see *Related Information*.



<a name="loio625d7733c30b4666b4a522d7fa68a550__section_plg_lvz_zgb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbrole" : { 
>    "plugin_name" : "com.sap.hana.di.role", 
>    "plugin_version": "4.0.0.0" 
> }, 
> "hdbroleconfig" : { 
>    "plugin_name" : "com.sap.hana.di.role.config", 
>    "plugin_version": "4.0.0.0" 
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Logical Schemas \(.hdblogicalschema and .hdblogicalschemaconfig\)](logical-schemas-hdblogicalschema-and-hdblogicalschemaconfig-fa9cda8.md "Transforms a design-time logical-schema definition into run-time database objects that can be used by synonyms and so on.")

