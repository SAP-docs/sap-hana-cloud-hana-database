<!-- loio519fdcd4075549889261bbf1b2e1dc36 -->

# Create a JSON Document Store

Set up a store in SAP HANA for your JSON documents.



<a name="loio519fdcd4075549889261bbf1b2e1dc36__prereq_u5n_fbz_tnb"/>

## Prerequisites

When creating an instance of the SAP HANA Document Store \(DocStore\) in SAP HANA Cloud, the following prerequisites apply:

-   The SAP HANA Cloud instance where you want to enable the Document Store is provisioned and available.
-   You have access to SAP BTP Cockpit.
-   You have the required permissions, for example, `Space Developer`.



## Context

The Document Store is a dedicated binary store that enables the storage and processing of data in JSON format in the SAP HANA Cloud database. You can use the Document Store to collect and maintain JSON documents, that is; text files formatted according to the rules defined in the JavaScript Object Notation. The Document Store also allows native operations on JSON documents, for example: filtering and aggregation, as well as joins with SAP HANA column-store or row-store tables.



## Procedure

1.  Check that the Document Store is enabled.

    The Document Store is enabled for a specific SAP HANA Cloud database, as follows:

    > ### Note:  
    > Enabling the JSON Document Store for a SAP HANA Cloud database starts an instance of the "`docstore`" service. No more than one `docstore` process is allowed in a database. For more details, see *Related Information* below.

    1.  Enable the JSON Document Store

        In SAP BTP Cockpit, navigate to the subaccount containing the SAP HANA Cloud instance provisioned for your Cloud Foundry space and then choose: *Actions* \> *Monitor Landscape* \> *Actions* \> *Edit*.

    2.  Navigate to *Additional Features* and check *Document Store*.

    3.  Save your changes to the configuration.


2.  Create a JSON collection in the Document Store using SQL.

    Open an SQL console and enter the following SQL command:

    ```sql
    create collection Customers;
    ```

3.  Create a JSON collection using a design-time artifact.

    You can define a JSON collection in a design-time artifact with the suffix “`hdbcollection`”, for example, `AUTHORS.hdbcollection`. The file format uses a DDL-style syntax which is equivalent to the corresponding `CREATE COLLECTION` SQL syntax, but without the leading `CREATE` command, as illustrated in the following example:

    > ### Code Syntax:  
    > `/src/AUTHORS.hdbcollection`
    > 
    > ```
    > COLLECTION "AUTHORS"
    > ```

    The `hdbcollection` artifact must be located in the `db/` module of your Document Storeltitarget application. Assuming that the corresponding HDI plug-in is available, the collection defined in the design-time artifact is activated in the catalog at application-deployment time.

    > ### Note:  
    > If the Document Store is not enabled and available at deployment time, the deployment operation fails and no collection object is created in the database catalog.


**Related Information**  


[Enabling Additional Features \(SAP HANA Cloud Getting Started Guide\)](https://help.sap.com/viewer/DRAFT/9ae9104a46f74a6583ce5182e7fb20cb/dev/en-US/e379ccd3475643e4895b526296235241.html)

[Maintaining JSON Collections in the SAP HANA Document Store](maintaining-json-collections-in-the-sap-hana-document-store-a8f6f34.md "The SAP HANA Document Store (DocStore) is used to store collections which contain one or more JSON artifacts (documents).")

[Add and Remove JSON Collections in the Document Store](add-and-remove-json-collections-in-the-document-store-fc6a0ab.md "Maintain new and existing collections of JSON documents in the SAP HANA Document Store.")

[Document Store Collections (.hdbcollection)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/fe16b635277c4aea825c72973f159359.html "Transforms a design-time document-collection resource into a collection database object.") :arrow_upper_right:

