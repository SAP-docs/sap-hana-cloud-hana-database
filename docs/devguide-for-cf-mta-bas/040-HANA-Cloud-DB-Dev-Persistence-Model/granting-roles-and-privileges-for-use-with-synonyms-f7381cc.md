<!-- loiof7381ccf4bc644f286ac72cc54a43478 -->

# Granting Roles and Privileges for Use with Synonyms

Assigning roles and privileges to object owners for applications that use synonyms to access external objects.

You can use the `.hdbgrants` configuration file to assign privileges to the owner of the synonym object and the application users \(consumers\) of the synonym's target objects in the same way as you would with the SQL `grant` statement.

> ### Tip:  
> If you use the artifact-creation Wizard in SAP Business Application Studio to create the new design-time `hdbgrants` artifact. the new artifact is displayed by default in the graphical editor. However, you can open the file in the code editor, too, or change the default setting. You can also choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_Codicon_go-to-file_b3beacd.svg) \(*Open Editor \(Code/UI\)\)* to toggle between the code and graphical editors. Changes made to the open artifact during the editing session are synchronized between both editors.

In the following example, <code>“EPM_XXX-table-grantor”</code> is a symbolic name for a user-defined service that executes the `GRANT` statement. The user-defined service must be specified in the `resources` section of the application project’s development-descriptor \(`mta.yaml`\).

> ### Sample Code:  
> `SNWD-table.hdbgrants`
> 
> ```
> {
>   "granting_service": {
>    "object_owner": { 
>       "schema_roles": [
>         {
>          "roles" : "EPM_XXX::RoleR1"
>         }
>       ]
>     },
>     "application_user": {
>       "schema_roles": [
>         {
>          "roles" : "EPM_XXX::RoleR2"
>         }
>       ]
>     }
>   }
> }
> 
> ```

On startup, the HDI Deployer looks for `.hdbgrants` \(and `.hdbrevokes`\) files and processes the contents in the following manner:

1.  For each grantor in the file, the HDI Deployer checks for the existence of a bound service with the specified name \(`"granting-service"` in the code sample above\)

2.  Connects to the database with the credentials of the named service

3.  Grants the specified privileges to the grantees.


> ### Note:  
> If the `"schema"` key is omitted for a privilege, then the `"schema"` property from the grantor service is used instead. If the `"name"` field in a `"global_object_privileges"` key of type `REMOTE SOURCE` is omitted, then the grantor's remote property is used instead.

In the `.hdbgrants` file, the top-level keys defines the **name** of the bound services which "**grant**" the specified privileges \(the "grantors"\), for example, `"granting-service"` in the code example above. The second-level keys define the users to whom the privileges must be granted \(the "grantees"\), for example, `"object_owner"` and `"application_user"`. The `"object_owner"` is used to specify the HDI container's object owner, and `"application_user"` defines the application users who are bound to the application modules, for example, the Node.js module. The third-level keys, for example, `"roles"`, are used to define the set of privileges to grant; the privileges are defined in a structure that is similar to that used in a role definition file \(`myRole.hdbrole`\).

> ### Tip:  
> For information about configuring a corresponding `.hdbrevokes` file that you can use to revoke granted permissions, see *Permissions for Objects in HDI Containers* in *Related Information* below. If both files exist, the `.hdbrevokes` file is processed before the `.hdbgrants` file. Since neither the `.hdbgrants` file nor the `.hdbrevokes` file is an HDI artifact, no HDI plug-in configuration is required to deploy them.



<a name="loiof7381ccf4bc644f286ac72cc54a43478__section_p3y_jwv_13b"/>

## The Granting Service

The first entry in the `hdbgrants` file \(<code>“granting-service”</code> in the code example above\) is the name of a service instance in your current Cloud Foundry space; this service instance executes the `GRANT` statement. The name specified can be either the name of an HDI container instance or the name of a user-provided service and must also be specified in the `resources` section of the multi-target application's development descriptor \(`mta.yaml`\).



### Defining the Granting Service in the Application Development Descriptor

If the HDI container needs a granting-service, then in addition to the service itself, the multi-target application's development descriptor \(`mta.yaml`\) must include the information the HDI Deployer needs to be able to find the privilege-granting service. The following information is required:

1.  `TARGET_CONTAINER`

    For the container specified in the `db` module, add a `TARGET_CONTAINER` property for the service that corresponds to the container.

2.  `modules`

    In the `modules` section, add a new `requires` entry for the granting-service.

3.  `resources`

    In the `resources` section, add a new entry for the granting service.


The following example of an `mta.yaml` file shows the modifications listed above which are required to define the granting service \(if the corresponding container needs such a service\):

> ### Sample Code:  
> Defining the Granting Service in the `mta.yaml` File
> 
> ```
> schema-version: '2.0' 
> ID: granting-service-example 
> version: 0.0.1 
> 
> modules:
>   - name: db 
>     type: hdb 
>     path: db  
>     requires: 
>       - name: hdi-container 
>         properties:                                    // #1.  
>           TARGET_CONTAINER: ~{hdi-container-service}   // #1.
>   
>       - name: granting-service                         // #2. 
> 
> resources:  
>   - name: hdi-container  
>     type: com.sap.xs.hdi-container 
>     properties: 
>       hdi-container-service: ${service-name} 
> 
>   - name: granting-service                             // #3. 
>     type: org.cloudfoundry.existing-service            // #3.
> ```



### Permitted Types of Granting Services

The HDI Deployer supports the following types of granting-services:

-   `hdi`

    An HDI container with access to the container's `GRANT` APIs. The corresponding service can be bound to the `db/` module application. The HDI Deployer recognizes the bound service by its `hdi_user` value in the credentials section and calls the container's API procedures to grant the privileges from the `.hdbgrants` file.

-   `sql`

    A technical database user with `GRANT` privileges for the required object privileges, roles, system privileges, etc.

    In this scenario, a 'user-provided service' must be created in the same space as the HDI container. The service needs to be set up with the permissions of a specified database user who can connect to the database and grant the privileges specified in the `.hdbgrants` files during application deployment. You can use the XS advanced command-line interface to create a user-provided \(granting\) service, as illustrated in the following example, where `xs cups` is an abbreviation for `xs create-user-provided-service`:

    ```
    cf cups grantor-service -p '{ "host": "host.acme.com", "port": "30015", 
    "certificate": "<myCertificate>", "user": "<TARGET_USER>", 
    "password": "Grant_123", "schema": "<TARGET_SCHEMA>", "tags": [ "hana" ] }'
    ```

    -   `"host"/"port"`

        Required for the connection to the database: `port` is the SQL port of the SAP HANA index server

    -   `"certificate"`

        If the database is configured to only accept secure connections, then the granting-service requires an SSL certificate that must be included in the user-provided service, for example, using the `"certificate":""` parameter.

    -   `"user"/"password"`

        Connection details for a database user that has grant permissions for the objects in the schema.

    -   `"schema"`

        The database schema that contains the objects to which access is to be granted.

    -   `"type"`

        The type of the grantor-service mechanism; valid values are: `"hdi"`, `"sql"`, or `"procedure"`. If the type is not specified, then the type is selected automatically based on the following rule: if the field `"hdi_user"` is present, then the type is set to `hdi`, otherwise, the type is set to `sql`.


-   `procedure`

    If the technical database user does not have `GRANT` privileges for the required object privileges, roles, system privileges, etc., but only `EXECUTE` privileges on a stored procedure which can grant the privileges, then the following prerequisites apply:

    -   At the database level, a `GRANT` procedure must exist \(or be visible\) in the schema which is used in the user-provided service.

    -   The technical database user must have `EXECUTE` privileges on the `GRANT` procedure.

    -   The name of the `GRANT` procedure must be specified in the user-provided service in the `"procedure"` field, for example:

        `"procedure": "GRANT"`.

    -   The schema name of the `GRANT` procedure can be specified in the user-provided service in the `"procedure_schema"` field, for example:

        `"procedure_schema": "A_SCHEMA"`.

    -   In this particular scenario, the user-provided service must contain a `"type"` field with the value `"procedure"`.


-   `ignore`

    Grant privileges have already been assigned at the database-level, so the HDI Deployer ignores the content of the `.hdbgrants` file.




<a name="loiof7381ccf4bc644f286ac72cc54a43478__section_chg_ctf_cy"/>

## The Object Owner

The <code>“object_owner”</code> property defines the roles to be assigned to the container's **object** owner. The name of the role differs according to whether the target object is in an application schema \(HDI application container\) or a classic SAP schema \(for example, ERP\).

> ### Sample Code:  
> `.hdbgrants` File for Role Assignment in a Classic Schema
> 
> ```json
> "object_owner": { 
>    "schema_roles": [
>     {
>      "roles" : "EPM_XXX::RoleR1"
>     }
>    ]
> },
> ```

If the synonym's target database object is in an application's HDI container, the owner of the object is the schema owner. HDI container schema owners have a special name that ends with the string “`#OO`” \(for example, `ContainerOwner#OO`\), the corresponding role must also have the suffix `#`, for example, `RoleR1#`, as illustrated in the following example:

> ### Sample Code:  
> `.hdbgrants` File for Role Assignment in an HDI Container Schema
> 
> ```json
> "object_owner": { 
>    "schema_roles": [
>     {
>      "roles" : "RoleR1#"
>     }
>    ]
> },
> ```

If a role name ends with “\#”, for example, `MyRole#`, the role definition \(specified in an `hdbrole` artifact\) is allowed to include “`WITH GRANT OPTION`” privileges as well as references to other roles whose names end with “\#”. The HDI container object owner needs most privileges “WITH GRANT OPTION”.



<a name="loiof7381ccf4bc644f286ac72cc54a43478__section_a2m_ctf_cy"/>

## The Application User

The <code>“application_user”</code> property defines the roles to be assigned to the user of the application that consumes the defined synonym and requires access to the corresponding schemas containing the target objects referenced by the synonym. The following example shows how to assign `application_user` to the privileges defined in the externally created role `"EPM_XXX::RoleR1"`.

> ### Sample Code:  
> `SNWD-table.hdbgrants`
> 
> ```json
> "application_user": {
>    "schema_roles": [
>     {
>      "roles" : "EPM_XXX::RoleR1"
>     }
>    ]
> }
> ```

> ### Tip:  
> <code>“application_user”</code>” does not refer to a real user; it refers to the technical user associated with the global “`access_role`” required for access to the corresponding run-time container. The “`access_role`” is assigned a set of default permissions for the run-time schema, for example: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `EXECUTE`, `CREATE TEMPORARY TABLE`, and `SELECT CDS METADATA`.



<a name="loiof7381ccf4bc644f286ac72cc54a43478__section_ey4_r1r_2y"/>

## Schema Roles

The `schema_roles` property is used to specify one or more schema-local <code>“roles”</code> to users by means of a grantor service. Access to the synonym's target object is enabled by assigning a local HDI container role that grants the container's object owner access to the target object in the foreign schema. This role must also have the `privileges_with_grant_option`, and for this reason the role name must end with the hash \(\#\) character, for example, `RoleR1#`. Assigning roles to an HDI schema owner requires some changes to the `.hdbgrants` file, as illustrated in the following example:

> ### Sample Code:  
> `SNWD-table.hdbgrants` for HDI Schema \(Container\) Roles
> 
> ```json
> {
>   "EPM_XXX-table-grantor": {
>    "object_owner": { 
>       "schema_roles": [
>        {
>         "roles" : "EPM_XXX::RoleR1#"
>        }
>       ]
>     },
>     "application_user": {
>       "schema_roles": [
>        {
>         "roles" : "EPM_XXX::RoleR1"
>        }
>       ]
>     }
>   }
> }
> 
> ```

Due to naming conventions in HDI, and the fact that the container role must provide the `GRANT` privileges, the name of the role-definition assigned to the HDI container's object owner must have the suffix "`#`", for example, <code>“MyRole#”</code>.

If a role name ends with the hash character \(`#`\), for example, `MyRole#`, the role definition can include “with-grant-option” privileges as well as references to other roles whose names also end with `#`. A role whose name ends with `#` can only be granted by means of the HDI APIs to a container’s object owner, for example, <code><i class="varname">&lt;container&gt;</i>#OO</code>.



<a name="loiof7381ccf4bc644f286ac72cc54a43478__section_typ_w1r_2y"/>

## Role Names

Use the <code>“roles”</code> property to specify the role \(or roles\) to be assigned to the object owner \(one per HDI container\) and application user by the grantor service, as illustrated in the following example:

> ### Sample Code:  
> `SNWD-table.hdbgrants`
> 
> ```json
> {
>   "EPM_XXX-table-grantor": {
>    "object_owner": { 
>       "schema_roles": [
>        {
>         "roles" : ["EPM_XXX::RoleR1#"]
>        }
>       ]
>     },
>     "application_user": {
>       "schema_roles": [
>        {
>         "roles" : ["EPM_XXX::RoleR1"]
>        }
>       ]
>     }
>   }
> }
> 
> ```

The attribute <code>“roles”</code> is used to specify the name of the role that defines the privileges to assign to users. The role name must be a non-empty string that contains only permitted characters.

In the `.hdbgrants` file, the following types of role names are possible:

-   <code><i class="varname">&lt;RoleName&gt;</i></code>

    If a role name does **not** end with the hash character \(`#`\), for example, `MyRole`, then only privileges without grant options can be included in the role as well as references to any only other roles whose names also do not end with “`#`”.

-   <code><i class="varname">&lt;RoleName&gt;</i>#</code>

    If a role name ends with the hash character \(`#`\), for example, `MyRole#`, it's corresponding role definition can include “with-grant-option” privileges as well as references to other roles whose names also end with `#`. A role whose name ends with `#` can only be granted by means of the HDI APIs to a container’s object owner, for example, <code><i class="varname">&lt;container&gt;</i>#OO</code>.


The roles specified in the `hdbgrants` file must already exist as objects in the database catalog. The corresponding role-definition must define the various privileges required for access to database objects, for example: system, schema, object, and analytic privileges. In HDI, you can define a user role with an `.hdbrole` artifact. You can also use alternative methods to define access privileges to database objects, for example, the SQL command `create role "EPM_XXX::external access`. In addition, you will also have to grant the `SELECT` privilege manually to each base objects referenced by the synonym.

> ### Caution:  
> To prevent unnecessary access to the schema via “definer-mode” objects \(procedures, views\), it is recommended to assign different roles to the object owner and the application user. The role for the object owner should provide `GRANT` options; the role for the application user should provide privileges for “invoker-mode” objects \(for example, invoker-mode procedures\).

**Related Information**  


[Enable Access to Objects in a Classic \(non-HDI\) Schema](enable-access-to-objects-in-a-classic-non-hdi-schema-402944b.md "Use a synonym to enable access to objects in a database schema that is not managed by SAP HDI (for example, ERP).")

[Syntax Options in the hdbgrants File](syntax-options-in-the-hdbgrants-file-f49c1f5.md "Assign the privileges required by users to access objects in the target schema.")

[Permissions for Objects in HDI Containers](permissions-for-objects-in-hdi-containers-79e8664.md "The owner of a container object needs additional privileges to the ones assigned by default.")

