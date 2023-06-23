<!-- loio8a82c9e9e22a4b67a51ff22097038aab -->

# Maintain Values in the SAP HANA Secure Store

Insert entries into \(and retrieve and remove entries from\) the SAP HANA Secure Store.



<a name="loio8a82c9e9e22a4b67a51ff22097038aab__prereq_yrs_ybb_fcb"/>

## Prerequisites

To maintain content in the SAP HANA Secure Store, bear in mind the following conditions:

-   The multitarget application must be bound to an instance of the `hana` service using the `securestore` service plan.

-   For multitarget applications, the resource type for the database connection specified in the MTA's deployment descriptor \(`mta.yaml` file\) must be `com.sap.xs.hana-securestore`.




## Context

In the context of the application run time, the SAP HANA Secure Store is used to maintain sensitive information such as user credentials. The stored procedures listed in the following table enable you to insert, retrieve, and delete entries in the Secure Store. Any application that is bound to an instance of the `hana` service with the service plan `securestore` has access to these stored procedures and can use them to maintain content stored in the Secure Store:

**Stored Procedures for Secure Store Maintenance**


<table>
<tr>
<th valign="top">

Stored Procedure



</th>
<th valign="top">

Description



</th>
<th valign="top">

Required Parameters



</th>
</tr>
<tr>
<td valign="top">

 `SYS.USER_SECURESTORE_INSERT` 



</td>
<td valign="top">

Insert an encrypted entry into the SAP HANA Secure Store.



</td>
<td valign="top">

`STORE_NAME`

`FOR_XS_APPLICATIONUSER`

`KEY`

`VALUE`



</td>
</tr>
<tr>
<td valign="top">

 `SYS.USER_SECURESTORE_RETRIEVE` 



</td>
<td valign="top">

Retrieve an encrypted entry from the SAP HANA Secure Store.



</td>
<td valign="top">

`STORE_NAME`

`FOR_XS_APPLICATIONUSER`

`KEY`

`VALUE`



</td>
</tr>
<tr>
<td valign="top">

 `SYS.USER_SECURESTORE_DELETE` 



</td>
<td valign="top">

Delete an encrypted entry from the SAP HANA Secure Store.



</td>
<td valign="top">

`STORE_NAME`

`FOR_XS_APPLICATIONUSER`

`KEY`



</td>
</tr>
</table>

> ### Tip:  
> For more information about the parameters required when calling the Secure-Store procedures, see *Related Information* below.

You can use Cloud Foundry applications or SAP HANA SQL to maintain entries in the SAP HANA Secure Store:



## Procedure

1.  Insert encrypted values into the SAP HANA Secure Store.

    You can use an application or SAP HANA SQL to insert encrypted values into the SAP HANA Secure Store by calling the stored procedure `SYS.USER_SECURESTORE_INSERT`.

2.  Retrieve encrypted values from the SAP HANA Secure Store.

    You can use an application or SAP HANA SQL to request entries from the SAP Secure Store by calling the stored procedure `SYS.USER_SECURESTORE_RETRIEVE`.

3.  Delete encrypted values from the SAP HANA Secure Store.

    You can use an application or SAP HANA SQL to remove entries from the SAP HANA Secure Store by calling the stored procedure `SYS.USER_SECURESTORE_DELETE`.

4.  Set up a secure connection to the SAP HANA Secure Store.

    To avoid authorization problems when the application tries to connect to the database, it is essential to ensure that the resource type for the database connection specified in the Multi-Target Application's development descriptor \(`mta.yaml` file\) is `com.sap.xs.hana-securestore`.


**Related Information**  


[SAP HANA Secure-Store Interface Procedures and Parameters](sap-hana-secure-store-interface-procedures-and-parameters-a847b4d.md "A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.")

[Access the SAP HANA Secure Store with Node.js](access-the-sap-hana-secure-store-with-node-js-be4db00.md "Use a Node.js application to maintain entries in the SAP HANA Secure Store.")

[Access the SAP HANA Secure Store with Java](access-the-sap-hana-secure-store-with-java-9210fd0.md "Use a Java application to maintain entries in the SAP HANA Secure Store.")

[Access the SAP HANA Secure Store with SQL](access-the-sap-hana-secure-store-with-sql-1dee8a9.md "Use SQL to maintain entries the SAP HANA Secure Store.")

