<!-- loio66a8d33fe06d47acbfafc0782c513d7b -->

# JSON Collections

JSON documents are grouped together as “collections ” that are stored in the SAP HANA Documentation Store \(DocStore\).



Data defined in documents formatted according to the JavaScript Object Notation \(JSON\) is stored in JSON artifacts that can be grouped into so-called “collections” and stored in the SAP HANA DocStore. The content of a JSON document may be deeply structured, however, unlike XML, a JSON document does not have a schema. This means that any valid JSON data may be inserted without first declaring its structure.

Document collections and the JSON content can be maintained with SQL in the same way as data stored in tables. For example, you can insert data with the `INSERT` statement and query the document data with the `SELECT` command. You can also use a single query statement to read data from tables and collections at the same time, and you can combine standard tables and JSON collections by joining them in the same way as the `JOIN` between any other column- or row-store tables.

Technically, collections are stored in a dedicated binary format; in SQL however, they are defined as tables with their own sub-type, which you can see by selecting collections on the basis of the table type `'COLLECTION'`, as illustrated in the following example:

```sql
SELECT * FROM tables WHERE table_type = 'COLLECTION'
```

The following example is included here to illustrate how a collection of customer details can be created, updated and read. The `INSERT` statement illustrates the syntax and structure of nested JSON data and the corresponding `SELECT` statements show the use of path expressions to navigate the content of the JSON document:

```sql
create collection Customers;
```

```sql
insert into Customers values({
    "name": 'Paul',
        "address": {
        "street": 'Main Street',
        "number": 10
        "city": 'Heidelberg'
        }
    });
```

```sql
select * from Customers where "address"."city" = 'Heidelberg';
```

```sql
select "address"."city", count(*) from Customers group by "address"."city";
```



<a name="loio66a8d33fe06d47acbfafc0782c513d7b__section_i3l_zl3_lpb"/>

## JSON Collection Index

You can create an index for a JSON document collection in the SAP HANA document store. The details of the collection index must be specified in a design-time `.hdbcollectionindex` artifact, and the SAP HDI plug-in `com.sap.hana.di.collection.index` is used to deploy the collection-index artifact to SAP HANA. The file format required in the `.hdbcollectionindex` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL statement “`CREATE HASH INDEX`”, but without the leading `CREATE` command, as illustrated in the following example:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbcollectionindex`
> 
> ```sql
> HASH INDEX "myIndex" ON "myCollection"("lastName")
> ```

For more information about the `.hdbcollectionindex` artifact and the corresponding HDI plug-in, see *Related Information* below.

**Related Information**  


[Add and Remove JSON Collections in the Document Store](add-and-remove-json-collections-in-the-document-store-fc6a0ab.md "Maintain new and existing collections of JSON documents in the SAP HANA Document Store.")

[The SAP HANA JSON Document Store](the-sap-hana-json-document-store-3872240.md "The SAP HANA Document Store contains JSON artifacts grouped in collections.")

[JSON Documents](json-documents-b79fda3.md "JSON documents are stored in the JSON Document Store (DocStore) and grouped into JSON collections.")

[Document Store Collections (.hdbcollection) - HDI Cloud Reference Guide](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_3_QRC/en-US/fe16b635277c4aea825c72973f159359.html "Transforms a design-time document-collection resource into a collection database object.") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA Database JSON Document Store Guide](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/2022_3_QRC/en-US/dca379e9c94940e998d9d4b5c656d1bd.html "This guide explains the SAP HANA JSON Document Store.") :arrow_upper_right:

[Document Store Collection Index (.hdbcollectionindex) - HDI Cloud Reference Guide](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_3_QRC/en-US/b4b1b5c8714a4af7a53e906a85c633f1.html "Transforms a design-time resource for a document collection index into a collection-index database object.") :arrow_upper_right:

