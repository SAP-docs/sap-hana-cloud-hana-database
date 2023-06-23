<!-- loiofe16b635277c4aea825c72973f159359 -->

# Document Store Collections \(.hdbcollection\)

Transforms a design-time document-collection resource into a collection database object.



The collection plug-in transforms a design-time, document-collection resource \(specified in a `.hdbcollection` artifact\) into a collection database object, which is a data store with the `table_type` “COLLECTION”. The file format required in the `.hdbcollection` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL statement “`CREATE COLLECTION`”, but without the leading `CREATE` command. The so-called “collections” are used to store JSON documents in the SAP HANA Document Store \(DocStore\).



<a name="loiofe16b635277c4aea825c72973f159359__section_erk_4vh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a JSON document store “collection” definition for HDI:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbcollection`
> 
> ```sql
> COLLECTION "CUSTOMERS"
> ```

> ### Note:  
> The `hdbcollection` artifact can only be used to create the JSON collection; it cannot be used to insert JSON documents into the collection.



<a name="loiofe16b635277c4aea825c72973f159359__section_nj3_nvh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbcollection" : {
>    "plugin_name" : "com.sap.hana.di.collection"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[SAP HANA Cloud JSON Document Store Guide](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/cloud/en-US/20d58a5f75191014b2fe92141b7df228.html)

