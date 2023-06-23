<!-- loio58fdf2d2ffae44b6a3dd0e9a3f5ae8c5 -->

# Indexes \(.hdbindex\)

Transform a design-time index resource into an index on a database table.



The index plug-in transforms a design-time index resource \(`.hdbindex`\) into an index on a database table. The file format required for `.hdbindex` artifacts uses a DDL-style syntax that is equivalent to the corresponding syntax in the SQL command `CREATE INDEX`, although without the leading “`CREATE`” command.



### Fuzzy Search Indexes

The HDI index plug-in can be reused to create fuzzy-search indexes if fach `*.hdbindex` file contains a single `CREATE FUZZY SEARCH INDEX` statement, as illustrated in the code samples included in the *Example Artifact Code* section below.

> ### Tip:  
> The plug-in can be used to create fuzzy search indexes for **all** search modes.

Multiple search indexes with different search modes can be created on a single column by adding multiple `*.hdbindex` files.



<a name="loio58fdf2d2ffae44b6a3dd0e9a3f5ae8c5__section_igp_xwh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time index definition for HDI:

> ### Code Syntax:  
> `/src/CUSTOMER_NAME_IDX.hdbindex`
> 
> ```json
> INDEX "com.sap.hana.example::CUSTOMER_NAME_IDX"
> ON "com.sap.hana.example::CUSTOMERS" (NAME)
> ```

To create a fuzzy-search index on a table created with `.hdbtable` where the HDI package is "`com.sap.hana.example`":

> ### Code Syntax:  
> File `/src/MY_TEXT_INDEX.hdbindex`
> 
> ```json
> FUZZY SEARCH INDEX "com.sap.hana.example::MY_TEXT_INDEX"
> ON "com.sap.hana.example::TAB1"(txt)
> SEARCH MODE TEXT
> ```



<a name="loio58fdf2d2ffae44b6a3dd0e9a3f5ae8c5__section_dl4_wwh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbindex" : {
>    "plugin_name" : "com.sap.hana.di.index"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[SAP HANA Cloud, SAP HANA Database Search Developer Guide](https://help.sap.com/docs/HANA_CLOUD_DATABASE/05c9edaee7fe4d28ab3627d0b1583df6/ce86ef2fd97610149eaaaa0244ca4d36.html)

