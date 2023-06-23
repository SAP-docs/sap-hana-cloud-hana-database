<!-- loio2bf9a6f2db824fbd84315196a9c318d5 -->

# SQL Views \(.hdbview\)

Transforms a design-time view resource into an SQL view database object.



The view plug-in transforms a design-time view resource \(defined in a `.hdbview` artifact\) into an SQL view database object. The file format required for the `.hdbview` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQLScript command `CREATE VIEW`, without the leading “`CREATE`”.



<a name="loio2bf9a6f2db824fbd84315196a9c318d5__section_gnz_313_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of an SQL view:

> ### Caution:  
> The use of the asterisk \(\*\) wildcard inside a view’s projection clause will be reported as a warning. This is because the use of the asterisk in the projection causes problems with the column ordering of underlying objects.

> ### Code Syntax:  
> `/src/active_customers.hdbview`
> 
> ```sql
> VIEW "com.sap.hana.example::ACTIVE_CUSTOMERS" 
> AS SELECT ID, NAME
> FROM "com.sap.hana.example::CUSTOMERS" 
> WHERE ACTIVE = '1'
> ```

SQL views also support “forward declarations” for database-level associations, for example, using the “`WITH ASSOCIATIONS`” clause, as illustrated in the following code snippet. The view plugin creates an additional intermediate “validate” artifact as part of the deployment process. This “validate” artifact positions itself between the view artifact, the artifacts which are referenced in the “`WITH ASSOCIATIONS`” clause, and the artifacts which consume the view artifact. The “validate” artifact attempts to validate the forward declared associations and issues a warnings if an association is not valid.

> ### Code Syntax:  
> `/src/view_with_associations.hdbview`
> 
> ```sql
> VIEW "com.sap.hana.example::CUSTOMERS2" 
> AS SELECT ID, NAME 
> FROM "com.sap.hana.example::CUSTOMERS" 
> WHERE ACTIVE = '1' 
> 
> WITH ASSOCIATIONS 
> ( 
>   JOIN OTHER_TABLE 
>   AS 
>   TO_OTHER_TABLE 
>   ON ID = TO_OTHER_TABLE.ID 
> )
> ```



<a name="loio2bf9a6f2db824fbd84315196a9c318d5__section_tg3_h13_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbview" : {
>    "plugin_name" : "com.sap.hana.di.view" 
> }
> ```

If the view selects from a synonym which points to an object inside another schema or different container, or to an object inside the same container but which is owned by a different user, then the container’s object owner \(“<code><i class="varname">&lt;container&gt;</i>#OO</code>”\) must have the required privileges on this target object, for example. `SELECT`, `UPDATE`, `INSERT`. If a view is exposed to other users, the object owner usually needs privileges `WITH GRANT OPTION`.

With this release, the use of `*` inside a view’s projection clause will be reported as a warning, because the use of `*` is not stable with regard to the column ordering of underlying objects. Views also support forward declarations for database-level associations using the `WITH ASSOCIATIONS` clause. The view plugin will create an additional intermediate “validate” artifact as part of the deployment. This “validate” artifact will position itself between the view artifact, the artifacts which are referenced in the WITH ASSOCIATIONS clause, and the artifacts which consume the view artifact. The “validate” artifact validates the forward declared associations and will issue a warnings in case an association is not valid.

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

