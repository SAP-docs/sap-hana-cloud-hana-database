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

