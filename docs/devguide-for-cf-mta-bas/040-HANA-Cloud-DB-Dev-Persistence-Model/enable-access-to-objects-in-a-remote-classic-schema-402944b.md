<!-- loio402944b21b7c4d60a825b3ac69479955 -->

# Enable Access to Objects in a Remote Classic Schema

Use a synonym to enable access to objects in a remote schema that is not managed by your Cloud Foundry application \(for example, ERP\).



## Prerequisites

To complete the steps described in this task, the following prerequisites apply:

-   You have access to the Cloud Foundry run-time environment

-   You have access to SAP Business Application Studio and the *SAP HANA Native Application* extension is installed in your development workspace.

-   -   You have access to the CF command-line interface client

-   You have access to a “classic” SAP database schema in a remote system \(for example, SAP NetWeaver EPM\)




## Context

You can enable a multitarget application to access objects in a remote schema; that is, a classic schema in a remote database. The target objects for the synonyms can be tables, views, functions, and procedures, as well as database sequences.

> ### Note:  
> For illustration purposes only, the target \(base\) objects used in this example are taken from SAP NetWeaver EPM content \(Sales Order Model\). However, you can substitute the target objects specified in the examples with your own target objects. Similarly, you can substitute the synonyms, roles, etc. specified in the examples with your own artifacts.



## Procedure

1.  Create the underlying target objects in the external schema \(for example, `EPM_DEV`\) to which the multitarget application's synonym points.

    The target objects can be tables, views, functions, procedures, and so on. You might have a number of tables in a schema, not all of which should be exposed by a synonym.

    > ### Tip:  
    > If the target objects already exist, you can skip this step.

2.  Create the roles to be granted for external access by means of the synonym.

    The following roles are required here:

    -   `external_access_g`

        Grant select privilege on schema `EPM_DEV` to "`EPM_XXX::external_access_g`" **with** grant option to allow access to the whole schema

        ```sql
        create role "EPM_XXX::external_access_g";
        grant select on SNWD_AD to "EPM_XXX::external_access_g" with grant option;
        grant select on SNWD_BPA to "EPM_XXX::external_access_g" with grant option;
        grant select on SNWD_PD to "EPM_XXX::external_access_g" with grant option;
        grant select on SNWD_PD_CATGOS to "EPM_XXX::external_access_g" with grant option;
        grant select on SNWD_SO to "EPM_XXX::external_access_g" with grant option;
        grant select on SNWD_SO_I to "EPM_XXX::external_access_g" with grant option;
        grant select on SNWD_SO_SL to "EPM_XXX::external_access_g" with grant option;
        ```

    -   `external_access_appuser`

        Grant select privilege on schema `EPM_DEV` to "`EPM_XXX::external_access_appuser`" to enable access **without** grant option to the whole schema.

        ```sql
        create role "EPM_XXX::external_access_appuser";
        grant select on SNWD_AD to "EPM_XXX::external_access_appuser";
        grant select on SNWD_BPA to "EPM_XXX::external_access_appuser";
        grant select on SNWD_PD to "EPM_XXX::external_access_appuser";
        grant select on SNWD_PD_CATGOS to "EPM_XXX::external_access_appuser";
        grant select on SNWD_SO to "EPM_XXX::external_access_appuser";
        grant select on SNWD_SO_I to "EPM_XXX::external_access_appuser";
        grant select on SNWD_SO_SL to "EPM_XXX::external_access_appuser";
        
        ```


3.  Create the synonym\(s\).

    You can create the synonym design-time object in a subfolder of your mulitarget application's database module, for example in <code>/<i class="varname">&lt;MyApp&gt;</i>/db/src/synonyms/SNWD.hdbsynonym</code>. In this example, we name the synonym definition `SNWD.hdbsynonym`, which contains multiple synonyms referencing tables/views in the target schema “`EPM_DEV`”.

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension in SAP Business Application Studio provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    > ### Sample Code:  
    > Synonym Definition \(`/MyApp/db/src/synonyms/SNWD.hdbsynonym`\)
    > 
    > ```json
    > {
    >   "SNWD_AD": {
    >     "target": {
    >       "object": "SNWD_AD",
    >       "schema": "EPM_DEV"
    >     }
    >   },
    >   "SNWD_BPA": {
    >     "target": {
    >       "object": "SNWD_BPA",
    >       "schema": "EPM_DEV"
    >     }
    >   },
    > 
    > [... synonyms {} ...]
    > 
    >   "SNWD_SO_SL": {
    >     "target": {
    >       "object": "SNWD_SO_SL",
    >       "schema": "EPM_DEV"
    >     }
    >   }
    > }
    > 
    > ```

4.  Grant access to the synonym's target objects \(for example, table\); the access can also be used by any views that “consume” the target objects.

    Access privileges are required on the target objects to which the synonym points. The type of access required \(`SELECT`/`EXECUTE`\) depends on the object type: `SELECT` for tables, views, and functions; `EXECUTE` for functions and procedures.

    The access mode is only relevant for target objects that are procedures and views. The access mode specifies the user whose privileges will be checked upon execution of the procedure. For procedures, the developer must explicitly specify the desired access mode \(for example, `DEFINER`/`INVOKER`\) when writing the procedure. Views are always DEFINER mode.

    Access can be enabled by referencing defined user roles with the <code>“roles”</code> property in an `.hdbgrants` file, as illustrated in the following example:

    > ### Caution:  
    > To prevent unwanted schema access, for example, via “definer-mode”, it is recommended to assign different roles to the object owner and the application user.

    > ### Sample Code:  
    > `myApp/db/cfg/epm_dev.hdbgrants` File
    > 
    > ```json
    > {
    >   "EPM_XXX-table-grantor": {
    >      "object_owner": {
    >            "roles": [
    >                "EPM_XXX::external_access_g"
    >            ]
    >      },
    >      "application_user": {
    >            "roles": [
    >                "EPM_XXX::external_access_appuser"
    >            ]
    >      }
    >   }
    > }
    > 
    > ```

    “`EPM_XXX-table-grantor`” is a symbolic name for a user-defined service that executes the `GRANT` statement. The user-defined service must be specified in the application project’s development-descriptor \(`mta.yaml`\). “`application_user`” refers to a technical access role; it is not a reference to a real user.

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    The role specified for assignment to <code>“object_owner”</code> should contain the `SELECT WITH GRANT OPTION` privilege on the corresponding target table; the role specified for assignment to <code>“application_user”</code> should specify the `SELECT` privilege \(**without** `GRANT OPTION`\) for the corresponding target tables, view, sequences, and `EXECUTE WITH GRANT OPTION` for the corresponding functions and procedures to enable access to the target objects via the synonyms created.

5.  Add references to <code>“EPM_XXX-table-grantor”</code> in the development descriptor \(`mta.yaml`\) for the application that needs to use the synonym \(to access the target objects\).

    > ### Sample Code:  
    > Application Development Descriptor \(`MyApp/mta.yaml`\)
    > 
    > ```
    > _schema-version: '2.0'
    > ID: syn-hdi-classic-1
    > version: 0.0.1
    > 
    > modules:
    >   - name: db
    >     type: hdb
    >     path: db
    >     requires:                                        # db module needs:
    >       - name: hdi-container                          # where synonyms are created
    >         properties:
    >           TARGET_CONTAINER: ~{hdi-container-service} 
    >           
    >       - name: EPM_XXX-table-grantor                  # for executing grant statement
    >           
    > resources:
    >   - name: hdi-container
    >     type: com.sap.xs.hdi-container
    >     properties:
    >       hdi-container-service: ${service-name}        
    > 
    >   - name: EPM_XXX-table-grantor
    >     type: org.cloudfoundry.existing-service         # service created with xs cups
    > 
    > ```

6.  Create a user-defined service \(for example, `EPM_XXX-table-grantor`\) in the multitarget application's developer space.

    The “user provided service” enables you to assign roles automatically to the generated users of the HDI container. The service uses the permissions assigned to a specified user to connect to a database and execute grant statements during application deployment. The grant statements are generated from content defined in an `.hdbgrants` file such as the one defined in a previous step.

    > ### Note:  
    > Platform services have access to any other service running in the same organization and space. This means that any service running in the same organization and space as the user-provided service you create in this step can use the user-provided service to access external objects.

    1.  Open a command shell and log on to the CF CLI with administrator privileges.

    2.  Change to the target space where you want to create the user-defined service.

        <code>cf target –s <i class="varname">&lt;SPACE&gt;</i></code>

    3.  Create the user-defined service `EPM_XXX-table-grantor`.

        ```
        cf cups EPM_XXX-table-grantor –p "{\"host\":\"host.acme.com\",\"port\":\"30015\",\"certificate\":\"<myCertificate>\", \"user\":\"EPM_DEV\",\"password\":\"Grant_123\",\"driver\":\"com.sap.db.jdbc.Driver\",\"tags\":[\"hana\"] , \"schema\" : \"EPM_XXX\" }"
        ```

        This command creates a user-defined service with the following configuration:

        ```json
        "EPM_XXX-table-grantor": [ 
          {
            "schema": "EPM_XXX", 
            "password": "Grant_123", 
            "driver": "com.sap.db.jdbc.Driver", 
            "port": "30015", 
            "host": "host.acme.com", 
            "user": "EPM_DEV", 
            "certificate":"<myCert>"
            "tags": [ "hana" ] 
          }
        ] 
        ```

        -   `"schema"`

            The database schema that contains the objects to which access is to be granted.

        -   `"user"/"password"`

            Connection details for a database user that has grant permissions for the objects in the schema.

        -   `"host"/"port"`

            Required for the connection to the database: `port` is the SQL port of the index server.

        -   `"driver"`

            Required to set up the client connection to the database

        -   `"certificate"`

            If the database is configured to only accept **secure** JDBC connections, then the grantor service requires an SSL certificate that must be included in the user-provided service, for example, using the <code>"certificate":"<i class="varname">&lt;myCertificate&gt;</i>"</code> parameter.

            > ### Tip:  
            > Starting with version 3.0.0 of the HDI deployer service, the `"host"`, `"port"`, and `"certificate"` parameters are no longer required since they can be obtained from the target container binding. In this case, you must only specify the `"user"`, `"password"`, and `"schema"` when creating the new user-provided service.


    4.  Check that the new user-defined service is running in the target space.

        Use the command `cf services` to display a list of services available in the current space; the following service should be visible:

        > ### Output Code:  
        > ```
        > cf services
        > 
        > Getting services in org "myorg" / space "DEV" as XSA_ADM...
        > Found services:
        > 
        > name                     service         plan      bound apps
        > --------------------------------------------------------------
        > EPM_XXX-table-grantor    user-provided
        > 
        > ```


7.  Build the multitarget application's DB module.

    You can use the tools included in SAP Business Application Studio.

8.  Consume the synonym\(s\) created so far.

    One obvious and simple way to consume synonyms is to use a view \(called `CUSTOMERS` in this example\) on a table.

    > ### Sample Code:  
    > View `/myApp/db/src/CUSTOMERS.hdbview`
    > 
    > ```sql
    > VIEW "CUSTOMERS" AS SELECT 
    > POSTAL_CODE, CITY, STREET, BUILDING 
    > FROM SNWD_AD
    > ```

9.  Check for the resulting objects in the database catalog.

    You can use the *Database Explorer* tools included in SAP Business Application Studio.

10. Create a role definition that enables access to the view.

    > ### Tip:  
    > The view is not **required** for the creation of a synonym; it is used here to test “consumption” of the synonym.

    > ### Sample Code:  
    > Role Definition `external_v_access.hdbrole`
    > 
    > ```json
    > { 
    >   "role": { 
    >     "name": "external_v_access", 
    >     "object_privileges": [ 
    >       { 
    >         "name":"CUSTOMERS", 
    >         "type":"VIEW", 
    >         "privileges":[ "SELECT" ] 
    >       }
    >     ]
    >   }
    > } 
    > ```

11. Assign the role to consumers of the view.

    The new role `external_v_access.hdbrole` must be assigned to the to the container-external user \(for example, `SYN_CONS`\) who needs access to the view \(in this example, `CUSTOMERS`\).

12. Test access to the view.

    Both the application user **and** the schema-external user should now have access to the view, which you can test by opening it in the *Database Explorer*.

    -   Application user

        With the container's access role, this user has access to all objects in the application container's run-time schema.

    -   Schema-external user

        Access to the view is granted by assignment of the role `external_v_access`.



**Related Information**  


[Database Synonyms in SAP HANA Cloud](database-synonyms-in-sap-hana-cloud-556452c.md "You can use synonyms in SAP HANA Cloud to enable access to objects that are not in the same schema or application container.")

[Syntax Options in the hdbgrants File](syntax-options-in-the-hdbgrants-file-f49c1f5.md "Assign the privileges required by users to access objects in the target schema.")

[Roles (.hdbrole and .hdbroleconfig)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/625d7733c30b4666b4a522d7fa68a550.html "Transform a design-time role resource (.hdbrole) into a run-time role object.") :arrow_upper_right:

[Enable Access to Objects in Another HDI Container](enable-access-to-objects-in-another-hdi-container-4adba34.md "Use a synonym to enable access to another HDI container.")

