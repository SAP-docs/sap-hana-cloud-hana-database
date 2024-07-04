<!-- loio6671c48d5f314417807aac11e6ae26cf -->

# Structured Filters \(.hdbstructuredfilter\)



The structured-filter plug-in transforms a design-time, DDL-based, structured-privilege resource \(defined in a `.hdbstructuredfilter` artifact\) into a structured-filter object in the database. The file format required for the `.hdbstructuredfilter` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE STRUCTURED FILTER`, but without the leading “`CREATE`”. The referenced views must be defined using the `WITH STRUCTURED PRIVILEGE CHECK` clause.



<a name="loio6671c48d5f314417807aac11e6ae26cf__section_y5w_s13_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time, structured-filter definition for HDI:

> ### Code Syntax:  
> `/src/USER_DATA_VIEW_FILTER.hdbstructuredfilter`
> 
> ```sql
> STRUCTURED FILTER USER_DATA_VIEW_FILTER 
> FOR SELECT ON USER_DATA_VIEW 
> WHERE USER_DATA_VIEW.USER_NAME = CURRENT_USER
> ```



<a name="loio6671c48d5f314417807aac11e6ae26cf__section_npv_r13_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbstructuredfilter" : {
>    "plugin_name" : "com.sap.hana.di.structuredfilter"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[CREATE STRUCTURED FILTER Statement (Data Definition)](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/2024_3_QRC/en-US/f0238ff8445342a8a9a2f9c3dd36631e.html "Create a structured filter to manage binding between a database object (SQL or parameterized SQL view) and static / dynamic filter condition under it.") :arrow_upper_right:

