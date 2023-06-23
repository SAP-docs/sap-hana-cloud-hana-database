<!-- loiob4b1b5c8714a4af7a53e906a85c633f1 -->

# Document Store Collection Indexes \(.hdbcollectionindex\)

Transforms a design-time resource for a document collection index into a collection-index database object.



The Collection Index plug-in creates an index \(specified in a `.hdbcollectionindex` artifact\) for a document collection \(specified in a `.hdbcollection` artifact\). Using the Collection plug-in, you can create new collections in the JSON Document Store using the `.hdbcollection` artifact. If you would like to add optional indexes to these document-collection artifacts, use the `.hdbcollectionindex` arfitact.

The file format required in the `.hdbcollectionindex` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL statement “`CREATE HASH INDEX`”, but without the leading `CREATE` command. For more information about the `CREATE HASH INDEX` statement, see *Related Information* below.

> ### Note:  
> The `.hdbcollectionindex` plug-in is only available for SAP HANA Cloud and requires SAP HDI \(Cloud\) feature version 1006, or later.



<a name="loiob4b1b5c8714a4af7a53e906a85c633f1__section_erk_4vh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a JSON Document Store “collection-index” definition for HDI:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbcollectionindex`
> 
> ```sql
> HASH INDEX "myIndex" ON "myCollection"("lastName")
> ```



<a name="loiob4b1b5c8714a4af7a53e906a85c633f1__section_nj3_nvh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbcollectionindex" : {
>    "plugin_name" : "com.sap.hana.di.collection.index"
> }
> ```

**Related Information**  


[CREATE HASH INDEX Statement](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/2021_01_QRC/en-US/ad9063aa6b6d479faac18bacb6caf145.html)

[Document Store Collections \(.hdbcollection\)](document-store-collections-hdbcollection-fe16b63.md "Transforms a design-time document-collection resource into a collection database object.")

