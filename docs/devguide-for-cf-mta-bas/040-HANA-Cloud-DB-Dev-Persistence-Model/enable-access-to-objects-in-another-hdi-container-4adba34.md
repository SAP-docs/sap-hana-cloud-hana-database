<!-- loio4adba34bd86544a880db8f9f1e32efb7 -->

# Enable Access to Objects in Another HDI Container

Use a synonym to enable access to another HDI container.



## Prerequisites

To complete the steps described in this task, the following prerequisites apply:

-   You have access to the application run-time environment.

-   You have access to SAP Business Application Studio and the *SAP HANA Native Application* extension is installed in your development workspace.




## Context

You can use a synonym in one application to enable access to database objects in a different application container; that is, objects in an HDI container that belongs to another application. You need to ensure access to the external HDI container and specify the type of privileges \(`SELECT`, `EXECUTE`\) required on the target object \(table, view, etc.\).

> ### Tip:  
> SAP Business Application Studio's *Guided Development* tool includes a tutorial called *Use Objects Contained in an External Database Schema* which shows you how to complete the individual steps in this task. You can find a link to the *Guided Development* tool on SAP Business Application Studio's *Welcome* screen or in the command palette \(*View* \> *Command Palette...* \> *Guided Development*\).



<a name="loio4adba34bd86544a880db8f9f1e32efb7__steps_g1b_qwk_cy"/>

## Procedure

1.  Locate the target object in the external schema to which the synonym will point.

    The target objects can be tables, views, functions, procedures, and so on; the target schema is another HDI container.

2.  Create the role definitions that enable access to the target database object.

    In this scenario, you create two roles:

    > ### Note:  
    > Both these roles must be created in the HDI schema that contains the target database object, for example, `Table_T1`.

    1.  Create a role for the schema owner of the application that contains the synonym.

        The role Role R1\# \(`Role_R1G.hdbrole`\) defines the privileges required for external access to a specific target object \(with grant option\); the role must be assigned to the user who needs access to the schema where the target object `Table_T1` is located. In this case, the access role is assigned to the owner of the schema containing the synonym that points to the target table.

        > ### Tip:  
        > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

        > ### Sample Code:  
        > Role Definition `Role_R1G.hdbrole` for HDI Schema Owner
        > 
        > ```json
        > { 
        >   "role": { 
        >     "name": "Role_R1G#", 
        >     "object_privileges": [ 
        >       { 
        >         "name":"<Table_T1>", 
        >         "type":"TABLE", 
        >         "privileges_with_grant_option":[ "SELECT" ] 
        >       }
        >     ]
        >   }
        > } 
        > ```

        > ### Tip:  
        > The hash character \(\#\) at the end of the role name signifies that the role is intended for assignment to a schema owner \(for example, <code><i class="varname">&lt;Container&gt;</i>#OO</code>\) and that the role must include the “`with grant option`” privilege.

    2.  Create a role for the user of the application which contains the synonym.

        The role `Role_R1.hdbrole` defines the privileges required by the application user who needs access to the target object `Table_T1` by means of a synonym; the “`SELECT`” privilege is required for the target object \(**without** grant option\). The role must be assigned to the user of the application which contains the synonym that needs access to the target object `Table_T1`.

        > ### Note:  
        > `Role_R1` is assigned to the application user by including a reference to it in `RoleR2`, which you define in a later step.

        > ### Sample Code:  
        > Role Definition `Role_R1.hdbrole` for application User
        > 
        > ```json
        > { 
        >   "role": { 
        >     "name": "Role_R1", 
        >     "object_privileges": [ 
        >       { 
        >         "name":"<Table_T1>", 
        >         "type":"TABLE", 
        >         "privileges":[ "SELECT" ] 
        >       }
        >     ]
        >   }
        > } 
        > ```


3.  Grant access to the schema containing the synonym's target object \(for example, `Table_T1`\).

    The owner of the schema containing the synonym requires `SELECT` privileges on the target object to which the synonym points. Access for the schema owner can be enabled in user roles which are then referenced with the <code>“container_roles”</code> property in an `.hdbgrants` file, as illustrated in the following example:

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    > ### Sample Code:  
    > Access-Granting Configuration File \(`myApp/db/cfg/Synonym_S1-table.hdbgrants`\)
    > 
    > ```json
    > {
    >   "EPM_log-table-grantor": {
    >      "object_owner": {
    >            "container_roles": [
    >                "Role_R1G#"
    >            ]
    >      },
    >      "application_user": {
    >            "container_roles": [
    >                "Role_R1"
    >            ]
    >      }
    >   }
    > }
    > ```

    > ### Caution:  
    > To prevent unwanted schema access, for example, via views, it is recommended to assign different roles to the object owner and the application user.

4.  Create the synonym\(s\).

    You can create the synonym design-time object in a subfolder of your application's database module, for example in <code>/<i class="varname">&lt;MyApp&gt;</i>/db/src/synonyms/</code>. In this example, we name the synonym definition `Synonym_S1.hdbsynonym`, which contains multiple synonyms referencing tables \(`Table_T1`, `Table_T2`, and `Table_T3`\), as illustrated in the following example:

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole``hdbroleconfig`, `hdbgrants`, and `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    > ### Sample Code:  
    > Synonym-Definition File \(`/MyApp/db/src/synonyms/Synonym_S1.hdbsynonym`\)
    > 
    > ```json
    > {
    >   "Table_T1": {}
    > }
    > ```

    > ### Note:  
    > In this example, the synonym configuration is not included in the synonym file; it is moved to the synonym's corresponding configuration file `SynonymS1.hdbsynonymconfig`, as described in the following step.

5.  Create a synonym configuration file.

    The synonym configuration can also be defined in a `.hdbsynonymconfig` file, for example, `myApp/db/cfg/Synonym_S1.hdbsynonymconfig`.

    > ### Note:  
    > The legacy `.hdbsynonymtemplate` files can also be used; they are converted to the `.hdbsynonymconfig` file format required at deployment time.

6.  Define details of the synonym configuration.

    andRather than defining a schema and a concrete schema name, you can use <code>“schema.configure”</code> to specify a path to a service name. The path expression is replaced at deployment time with the name of the schema of the referenced service. For example, in the following code example, <code>“schema.configure”</code> is replaced with schema used by the grantor service.

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    > ### Sample Code:  
    > Synonym Configuration File \(`myApp/db/cfg/Synonym_S1.hdbsynonymconfig`\)
    > 
    > ```json
    > 
    > { 
    >   "Table_T1": { 
    >     "target": { 
    >       "object": "Table_T1", 
    >       "schema.configure" : "EPM_log-table-grantor/schema" 
    >     }
    >   },
    >   […] 
    > } 
    > ```

7.  Define the required HDI plug-in configuration for the synonym.

    Add the application project’s central HDI plugin-configuration file \(`.hdbconfig`\) to the database module’s “`cfg/`” folder. You can copy the HDI plugin-configuration file from `myapp/db/src/.hdbconfig` to `myapp/db/cfg/.hdbconfig`.

    The `.hdiconfig` configuration file should include the following entries:

    > ### Sample Code:  
    > HDI Plug-in Configuration File \(`.hdiconfig`\)
    > 
    > ```json
    > "hdbsynonym" : { 
    >    "plugin_name" : "com.sap.hana.di.synonym", 
    >    "plugin_version": "2.0.0.0" 
    > }, 
    > "hdbsynonymconfig" : { 
    >    "plugin_name" : "com.sap.hana.di.synonym.config", 
    >    "plugin_version": "2.0.0.0" 
    > }
    > ```

    > ### Tip:  
    > The `"plugin_version": "2.0.0.0"` property is optional; from SAP HANA 2.0, the version of all plugins shipped with SAP HANA is the same as \(and equal to\) the SAP HANA version.

8.  Update the application's development descriptor \(`mta.yaml`\).

    Add references to “<code><i class="varname">&lt;target-hdi-container service name&gt;</i></code>” in the development descriptor for the application that needs to use the synonym to access the target objects, as illustrated in the example below.

    > ### Sample Code:  
    > Application Development Descriptor \(`MyApp/mta.yaml`\)
    > 
    > ```
    > modules: 
    >   - name: db
    >     type: hdb 
    >     path: db 
    >     requires:  
    >       - name: hdi-container                            
    >         properties: 
    >           TARGET_CONTAINER: ~{hdi-container-service} 
    > 
    >       - name: EPM_XXX-table-grantor
    >         group: SERVICE_REPLACEMENTS                 
    >         properties: 
    >           key: EPM_log-table-grantor
    >           service: ~{EPM_Synonym_S1-table-grantor-service} 
    > 
    > resources: 
    >   - name: hdi-container 
    >     type: com.sap.xs.hdi-container 
    >     properties: 
    >       hdi-container-service: ${service-name}
    >           
    >   - name: EPM_XXX-table-grantor 
    >     type: org.cloudfoundry.existing-service
    >     properties:            
    >       EPM_Synonym_S1-table-grantor-service: ${service-name}
    >     parameters:
    >       service-name: <HDI_Container_Name>-hdi-container
    > ```

9.  Bind the table-grantor service to your application project.

    In the *SAP HANA PROJECTS* tab, expand the project's *Database Connections* node, select the service to which you want to bind your application \(for example, ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_dependencyNotBound_1694e4a.svg) *EPM\_XXX-table-grantor*\), and choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_bind_074ce84.svg) \(*Bind*\).

10. Consume the synonym you created.

    One way to consume synonyms from inside the application's schema is to use a view \(for example, `View_V1`\) on the target table.

    > ### Sample Code:  
    > SQL View `/myApp/db/src/View_V1.hdbview`
    > 
    > ```sql
    > VIEW "View_V1" AS SELECT * FROM Table_T1
    > ```

11. Create a role definition that enables access to the view consuming `Synonym_S1`.

    > ### Tip:  
    > `Role_R2` must be located in the same HDI schema as the synonym. The view is not **required** for the creation of a synonym; it is used here to test “consumption” of the synonym `Synonym_S1`.

    The role definition \(for example, `Role_R2.hdbrole`\) must be assigned to the application users who need access to the view \(in this example, `View_V1`\). The application user already has access to the view through the application container's `access_role`; the role `Role_R2.hdbrole` is required by users outside of the application.

    > ### Sample Code:  
    > Role Definition `myApp/db/src/Role_R2.hdbrole`
    > 
    > ```json
    > { 
    >   "role": { 
    >     "name": "Role_R2", 
    >     "object_privileges": [ 
    >       { 
    >         "name":"View_V1", 
    >         "type":"VIEW", 
    >         "privileges":[ "SELECT" ] 
    >       }
    >     ]
    >   }
    > } 
    > ```

12. Build both application projects: the application that contains the target table \(`Table_T1`\) and the application that contains `Synonym_S1` and `View_V1`.

13. Check the database catalogs to ensure the appropriate objects exist and are accessible with the synonyms you created.


**Related Information**  


[Using Synonyms to Access External Schemas and Objects](using-synonyms-to-access-external-schemas-and-objects-bdc9f7a.md "Deploy synonyms to enable cross-container access to external objects.")

[Database Synonyms in SAP HANA Cloud](database-synonyms-in-sap-hana-cloud-556452c.md "You can use synonyms in SAP HANA Cloud to enable access to objects that are not in the same schema or application container.")

[Syntax Options in the hdbgrants File](syntax-options-in-the-hdbgrants-file-f49c1f5.md "Assign the privileges required by users to access objects in the target schema.")

[Users, Privileges, and Schemas](users-privileges-and-schemas-a260b05.md "A short overview of which properties, users, and privileges are involved when using synonyms in your SAP HANA application.")

