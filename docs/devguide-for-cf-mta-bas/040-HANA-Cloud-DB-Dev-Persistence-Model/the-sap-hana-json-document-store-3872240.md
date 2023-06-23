<!-- loio3872240967ec4e4ea030524985dac73b -->

# The SAP HANA JSON Document Store

The SAP HANA Document Store contains JSON artifacts grouped in collections.



In most common scenarios, data is stored in table with columns and rows, where for each column a strict definition or schema specifies the required layout and data types. These tables are "flat" in the sense that they are neither deeply nested nor hierarchical, and often it is necessary to define joins between multiple tables. For JSON documents, however, SAP HANA provides a Document Store: an independent store in addition to SAP HANA's well known Column Store and the Row Store.

> ### Note:  
> The Document Store is exclusively for use with JSON artifacts; it cannot be used to manage other document types, for example, text or PDF files.

Unlike SAP HANA's Column and Row Stores, where data is stored in tables, in the Document Store JSON data is stored in so-called "collections". In a collection, the stored data describes its own structure; the data can be nested \(deeply, if required\); and there is no **a priori** definition of which fields exist or which data type the fields are associated with.

If your data is JSON and you need to store it, for long-term processing or for intermediates, the Document Stores is beneficial; it allows you to work on JSON data using filters, offers native aggregation, and allows you to use your JSON data in other SAP HANA engines, too. For example, you can join your JSON data in hierarchies, graphs, and spatial scenarios.

The SAP HANA Document Store is an ordinary SAP HANA service. A single transaction can span all defined stores \(for example, Row Store, Column Store, and Document Store\), and commits are atomic with no restrictions on any of the four ACID transaction properties.

The Document Store is an optional feature of the SAP HANA database which you have to enable for each SAP HANA Cloud database. Only one, single Document Store process per SAP HANA Cloud database is possible. To create the Document Store you can use the SAP BTP Cockpit to modify the configuration of your SAP HANA Cloud instance, for example, by enabling the Document Store as an additional feature. For more information, see *Related Information* below.

**Related Information**  


[Create a JSON Document Store](create-a-json-document-store-519fdcd.md "Set up a store in SAP HANA for your JSON documents.")

[Maintaining JSON Collections in the SAP HANA Document Store](maintaining-json-collections-in-the-sap-hana-document-store-a8f6f34.md "The SAP HANA Document Store (DocStore) is used to store collections which contain one or more JSON artifacts (documents).")

[JSON Collections](json-collections-66a8d33.md "JSON documents are grouped together as “collections ” that are stored in the SAP HANA Documentation Store (DocStore).")

[SAP HANA Cloud, SAP HANA Database JSON Document Store Guide](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/2023_2_QRC/en-US/dca379e9c94940e998d9d4b5c656d1bd.html "This guide explains the SAP HANA JSON Document Store.") :arrow_upper_right:

