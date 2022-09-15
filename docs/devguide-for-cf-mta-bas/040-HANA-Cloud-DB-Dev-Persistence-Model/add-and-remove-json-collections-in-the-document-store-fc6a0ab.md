<!-- loiofc6a0ab114c8416eb561c9b5aba8fc7d -->

# Add and Remove JSON Collections in the Document Store

Maintain new and existing collections of JSON documents in the SAP HANA Document Store.



<a name="loiofc6a0ab114c8416eb561c9b5aba8fc7d__prereq_u5n_fbz_tnb"/>

## Prerequisites

For adding and removing JSON collections from the SAP HANA Document Store \(DocStore\), the following prerequisites apply:

-   The Document Store is enabled and running in your SAP HANA Cloud instance.

    > ### Tip:  
    > For information about how to create and enable the Document Store in SAP HANA Cloud, see *Related Information* below.




## Context

The Document Store allows native operations on JSON documents, for example: filtering and aggregation, as well as joins with SAP HANA column-store or row-store tables. You can use standard SQL commands in an SQL console to maintain the document collections in the SAP HANA Document Store and, in addition, the JSON documents that make up the collection. For example, you can add, update, and remove JSON documents in a collection. You can also maintain the values defined in the individual JSON documents.



<a name="loiofc6a0ab114c8416eb561c9b5aba8fc7d__steps_f2q_rnc_sy"/>

## Procedure

1.  Create a JSON collection in the Document Store.

    To create a collection of JSON documents called “CUSTOMERS” run the following command as administrator in an SQL console:

    ```sql
    CREATE COLLECTION CUSTOMERS;
    ```

    > ### Note:  
    > For more information about the SQL statements used in this tutorial, see *Related Information* below.

2.  Insert a JSON document into the collection.

    Insert JSON-formatted information into the collection, as illustrated in the following example:

    > ### Sample Code:  
    > ```json
    > insert into Customers values({
    >     "firstName": 'Kofi', 
    >     "familyName": 'Tetteh', 
    >     "address": { 
    >         "street": 'Nkrumah Close',
    >         "number": 10, 
    >         "city": 'Kumasi'
    >         },
    >     "details": { 
    >         "age": 43 
    >         } 
    >     }); 
    > ```

    > ### Sample Code:  
    > ```json
    > insert into Customers values({
    >     "firstName": 'Kwame', 
    >     "familyName": 'Asumang', 
    >     "address": { 
    >         "street": 'Independence Avenue',
    >         "number": 1957,  
    >         "city": 'Kumasi'
    >         },
    >     "details": { 
    >         "age": 27 
    >         } 
    >     }); 
    > ```

3.  Run a query on the content of a JSON document in the Document Store.

    Search the JSON collection for information about specific addresses, as illustrated in the following example:

    > ### Sample Code:  
    > ```sql
    > select * from Customers where "address"."city" = 'Kumasi;
    > ```

    > ### Sample Code:  
    > ```sql
    > select * from Customers where "details"."age" = 40;
    > ```

4.  Update individual JSON documents in a collection.

    To update a JSON documents stored in the JSON collection “CUSTOMERS”, use the `UPDATE` command as follows, which specifies what values to change \(`SET`\) in the JSON documents, where \(`Customers`\), and on what basis \(age\):

    > ### Sample Code:  
    > ```sql
    > UPDATE Customers SET Customers = { "name": 'Kojo', "age": 50 } where "details"."age" > 30;
    > 
    > ```

    The result of this change request in the JSON collection is as follows:

    > ### Sample Code:  
    > ```json
    > { "firstName": "Kojo", "age": 50 }
    > { "firstName": "Kwame", "familyName": "Asumang", "address": { "street": "Independence Avenue", "number": 1957, "city": "Kumasi" }, "details": { "age": 27 } }
    > ```

5.  Remove JSON documents from a collection.

    To remove JSON documents stored in the collection “CUSTOMERS”, use the `DELETE FROM` command as follows, where all documents that match the condition defined in the `WHERE` clause are deleted:

    > ### Sample Code:  
    > ```sql
    > DELETE FROM CUSTOMERS WHERE <condition>;
    > 
    > ```

    To remove all documents from a JSON collection, use the following command, in which `WHERE true` is implied:

    > ### Sample Code:  
    > ```sql
    > DELETE FROM CUSTOMERS;
    > 
    > ```

6.  Rename a JSON document collection.

    To rename an existing JSON collection, use the following command:

    > ### Sample Code:  
    > ```sql
    > RENAME COLLECTION <collection_name> TO <new_collection_name>; 
    > ```

7.  Remove a JSON document collection.

    To drop an existing JSON collection table from the database, use the following command:

    > ### Note:  
    > Dropping a JSON collection removes from the database all the JSON documents that are stored in the collection, too.

    > ### Sample Code:  
    > ```sql
    > DROP COLLECTION <collection_name>; 
    > ```


**Related Information**  


[Create a JSON Document Store](create-a-json-document-store-519fdcd.md "Set up a store in SAP HANA for your JSON documents.")

[Maintaining JSON Collections in the SAP HANA Document Store](maintaining-json-collections-in-the-sap-hana-document-store-a8f6f34.md "The SAP HANA Document Store (DocStore) is used to store collections which contain one or more JSON artifacts (documents).")

[SAP HANA Cloud, SAP HANA Database JSON Document Store Guide](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/2022_3_QRC/en-US/dca379e9c94940e998d9d4b5c656d1bd.html "This guide explains the SAP HANA JSON Document Store.") :arrow_upper_right:

