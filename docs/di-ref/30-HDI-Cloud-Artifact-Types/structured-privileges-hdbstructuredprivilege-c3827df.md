<!-- loioc3827df3a9dc4c45b5b4e2f7b1070b08 -->

# Structured Privileges \(.hdbstructuredprivilege\)

Transforms a design-time DDL-based structured privilege resource into a structured privilege object.



The structured-privilege plug-in transforms a design-time, DDL-based, structured-privilege resource \(defined in a `.hdbstructuredprivilege` artifact\) into a structured-privilege object in the database. The file format required for the `.hdbstructuredprivilege` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE STRUCTURED PRIVILEGE`, but without the leading “`CREATE`”. The referenced views must be defined using the `WITH STRUCTURED PRIVILEGE CHECK` clause.



<a name="loioc3827df3a9dc4c45b5b4e2f7b1070b08__section_y5w_s13_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time, structured-privilege definition for HDI:

> ### Code Syntax:  
> `/src/USER_DATA_VIEW_PRIVILEGE.hdbstructuredprivilege`
> 
> ```sql
> STRUCTURED PRIVILEGE USER_DATA_VIEW_PRIVILEGE 
> FOR SELECT ON USER_DATA_VIEW 
> WHERE USER_DATA_VIEW.USER_NAME = CURRENT_USER
> ```



<a name="loioc3827df3a9dc4c45b5b4e2f7b1070b08__section_yj2_wth_k1c"/>

## Wildcards

The file format also allows the use of wildcards, as shown in the following example:

> ### Code Syntax:  
> ```sql
> STRUCTURED PRIVILEGE PRIVILEGE_NAME 
> FOR SELECT ON <object_identifier>[, <object_identifier>] 
> [ ESCAPE '\' ] 
> [ LIKE <wildcard_object_identifier>[, <wildcard_object_identifier>] 
> [ NOT LIKE <wildcard_object_identifier>[, <wildcard_object_identifier>] ] ] 
> WHERE | CONDITION PROVIDER
> ```

Note the following important points:

-   Using `ESCAPE` followed by a single quoted character defines the escape character which can be used to escape wildcards.

-   Any `wildcard_object_identifiers` specified in the `NOT LIKE` section require corresponding `wildcard_object_identifiers` in the `LIKE` section, i.e. `NOT LIKE` should only exclude matches made due to `LIKE` conditions.

-   A `wildcard_object_identifier` must be wrapped in double quotes \(""\) and must be schema-local \(i.e. `"someSchema"."V%1"` is not allowed\).

-   The use of `wildcard_object_identifiers` requires at least one valid `object_identifier` \(defined in the “`SELECT ON`” clause\).

-   The `NOT LIKE` section can only be used if `wildcard_object_identifiers` in the `LIKE` section are specified; the `NOT LIKE` section is used to restrict the set of views declared in the `LIKE` section.

-   Valid wildcards are '\_' \(underscore character\) and '%' \(percentage character\).


> ### Tip:  
> The `wildcard_object_identifiers` specified in the `LIKE` section are used to define an `OR` query. The `wildcard_object_identifiers` in the `NOT LIKE` section are used to define an `AND NOT` query.

For example, the wildcards declared in the `LIKE` and `NOT LIKE` sections of the following code sample:

> ### Code Syntax:  
> ```sql
> LIKE obj1, obj2, … objN 
> NOT LIKE notObj1, notObj2, … notObjM
> ```

correspond logically to the following syntax:

> ### Code Syntax:  
> ```sql
> (obj1 or obj2 or … or objN) AND NOT (notObj1 or notObj2 or … or notObjM)
> ```



<a name="loioc3827df3a9dc4c45b5b4e2f7b1070b08__section_pr1_rvh_k1c"/>

## Example Artifact Code with Wildcards

It is also possible to use wildcards according to the format shown in the following example:

> ### Code Syntax:  
> `/src/USER_DATA_VIEW_PRIVILEGE_WILDCARD.hdbstructuredprivilege`
> 
> ```sql
> STRUCTURED PRIVILEGE USER_DATA_VIEW_PRIVILEGE_WILDCARD 
> FOR SELECT ON USER_DATA_VIEW 
> ESCAPE '\' 
> LIKE "USER\_Data\_VIEW1%", "USER\_Data\_VIEW2%" 
> NOT LIKE "USER_Data_VIEW1\%"
> WHERE USER_DATA_VIEW.USER_NAME = CURRENT_USER
> ```

Here, in addition to the former definition, all views with a structured privilege check that start with `USER_Data_VIEW1` or `USER_Data_VIEW2` \(excluding the `USER_Data_VIEW1` view\) should automatically be added. A view `USERsData_VIEW1` is also not detected because the underscore \('\_'\) was escaped.

Errors might occur if the conditions provided by the `WHERE` clause cannot be performed on some of these views. In that case, exclude them using the "`NOT LIKE`" section.



<a name="loioc3827df3a9dc4c45b5b4e2f7b1070b08__section_npv_r13_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbstructuredprivilege" : {
>    "plugin_name" : "com.sap.hana.di.structuredprivilege"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

