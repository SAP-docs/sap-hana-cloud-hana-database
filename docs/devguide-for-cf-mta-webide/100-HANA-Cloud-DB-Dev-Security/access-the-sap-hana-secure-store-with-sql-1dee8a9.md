<!-- loio1dee8a9f0c664da1985d9b8dccf57f1a -->

# Access the SAP HANA Secure Store with SQL

Use SQL to maintain entries the SAP HANA Secure Store.



<a name="loio1dee8a9f0c664da1985d9b8dccf57f1a__context_eg1_pdb_mgb"/>

## Context

In the context of the application run time, the SAP HANA Secure Store is used to maintain sensitive information such as user credentials. Access to the SAP HANA Secure Store is enabled by stored procedures which you can use to insert, retrieve, and delete entries in the Secure Store.

> ### Tip:  
> For more information about the parameters required when calling the Secure-Store procedures, see *Related Information* below.

The following examples show how to use SQL to maintain entries in the SAP HANA Secure Store:



<a name="loio1dee8a9f0c664da1985d9b8dccf57f1a__steps_fg1_pdb_mgb"/>

## Procedure

1.  Insert encrypted values into the SAP HANA Secure Store.

    The following example shows how to use SQL to call the stored procedure that inserts encrypted entries into the SAP HANA Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_INSERT \(SQL Application\)
    > 
    > ```sql
    > call SYS.USER_SECURESTORE_INSERT ('TestStoreName', False, 'TestKey', 'ab2467cdef'); 
    > ```

    > ### Note:  
    > When using SQL to insert entries into the SAP HANA Secure Store, key values must be provided in hexadecimal form.

2.  Retrieve encrypted values from the SAP HANA Secure Store.

    The following example shows how to use SQL to call the stored procedure that retrieves encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Stored Procedure USER\_SECURESTORE\_RETRIEVE \(SQL Application\)
    > 
    > ```sql
    > call SYS.USER_SECURESTORE_RETRIEVE ('TestStoreName', False, 'TestKey', ?); 
    > ```

3.  Delete encrypted values from the SAP HANA Secure Store.

    The following example shows how to use SQL to call the stored procedure that deletes encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Stored Procedure SYS.USER\_SECURESTORE\_DELETE \(SQL Application\)
    > 
    > ```sql
    > call SYS.USER_SECURESTORE_DELETE ('TestStoreName', False, 'TestKey'); 
    > ```


**Related Information**  


[Maintain Values in the SAP HANA Secure Store](maintain-values-in-the-sap-hana-secure-store-8a82c9e.md "Insert entries into (and retrieve and remove entries from) the SAP HANA Secure Store.")

[SAP HANA Secure-Store Interface Procedures and Parameters](sap-hana-secure-store-interface-procedures-and-parameters-a847b4d.md "A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.")

