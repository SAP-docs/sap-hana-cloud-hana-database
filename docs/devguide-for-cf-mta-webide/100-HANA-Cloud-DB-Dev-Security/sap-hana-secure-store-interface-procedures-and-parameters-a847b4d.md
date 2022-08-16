<!-- loioa847b4da7f6b4e8c9af3bf5e39c8ecfe -->

# SAP HANA Secure-Store Interface Procedures and Parameters

A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.



An application that is bound to an instance of the `hana` service with the service plan `securestore` has access to the following stored procedures, which enable encrypted access to the SAP HANA Secure Store:

-   `SYS.USER_SECURESTORE_INSERT`

-   `SYS.USER_SECURESTORE_RETRIEVE`

-   `SYS.USER_SECURESTORE_DELETE`


The information in the following sections describes the parameters available to make use of these interfaces to the SAP HANA Secure Store.

> ### Tip:  
> The information in this section is displayed in the `DEFINITION` column of the SAP HANA System view `PROCEDURES`.



<a name="loioa847b4da7f6b4e8c9af3bf5e39c8ecfe__section_ims_zlk_3gb"/>

## SYS.USER\_SECURESTORE\_INSERT

The following table lists the parameters used to describe an entry inserted into the SAP HANA Secure Store with the procedure `SYS.USER_SECURESTORE_INSERT`:


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Direction



</th>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

STORE\_NAME



</td>
<td valign="top">

IN



</td>
<td valign="top">

NVARCHAR\(530\)



</td>
<td valign="top">

The name of the target secure store for the insert operation



</td>
</tr>
<tr>
<td valign="top">

FOR\_XS\_APPLICATIONUSER



</td>
<td valign="top">

IN



</td>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

Indicates if the inserted value is stored for the application user \(“true”\) or the technical database user \(“false”\).

> ### Note:  
> If `FOR_XS_APPLICATIONUSER` is set to “true”, the session variable *<XS\_APPLICATIONUSER\>* must be set, too.



</td>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

IN



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

The key to be inserted into the target secure store \(`STORE_NAME`\)



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

IN



</td>
<td valign="top">

VARBINARY\(5000\)



</td>
<td valign="top">

The binary value of the entry to be inserted into the secure store. Non-binary values \(numbers, dates, strings\) must be converted, for example, using `TO_BINARY` in the database or by using a JavaScript Buffer to maintain the request body content.



</td>
</tr>
</table>



<a name="loioa847b4da7f6b4e8c9af3bf5e39c8ecfe__section_z2j_hnk_3gb"/>

## SYS.USER\_SECURESTORE\_RETRIEVE

The following table lists the parameters used to describe an entry retrieved from the SAP HANA Secure Store with the procedure `SYS.USER_SECURESTORE_RETRIEVE`:


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Direction



</th>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

STORE\_NAME



</td>
<td valign="top">

IN



</td>
<td valign="top">

NVARCHAR\(530\)



</td>
<td valign="top">

The name of the target secure store for the retrieve operation



</td>
</tr>
<tr>
<td valign="top">

FOR\_XS\_APPLICATIONUSER



</td>
<td valign="top">

IN



</td>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

Indicates if the retrieved value is stored for the application user \(“true”\) or the technical database user \(“false”\).

> ### Note:  
> If `FOR_XS_APPLICATIONUSER` is set to “true”, the session variable *<XS\_APPLICATIONUSER\>* must be set, too.



</td>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

IN



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

The key to be retrieved from the target secure store \(`STORE_NAME`\)



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

OUT



</td>
<td valign="top">

VARBINARY\(5000\)



</td>
<td valign="top">

The binary value of the entry to be retrieved from the secure store. Binary values can be converted for further use, for example, with `TO_NVARCHAR` in the database or by using a JavaScript Buffer to maintain the request body content.



</td>
</tr>
</table>



<a name="loioa847b4da7f6b4e8c9af3bf5e39c8ecfe__section_apk_hnk_3gb"/>

## SYS.USER\_SECURESTORE\_DELETE

The following table lists the parameters used to describe an entry removed from the SAP HANA Secure Store with the procedure `SYS.USER_SECURESTORE_DELETE`:


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Direction



</th>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

STORE\_NAME



</td>
<td valign="top">

IN



</td>
<td valign="top">

NVARCHAR\(530\)



</td>
<td valign="top">

The name of the target secure store for the delete operation



</td>
</tr>
<tr>
<td valign="top">

FOR\_XS\_APPLICATIONUSER



</td>
<td valign="top">

IN



</td>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

Indicates if the value to be deleted is stored for the application user \(“true”\) or the technical database user \(“false”\).

> ### Note:  
> If `FOR_XS_APPLICATIONUSER` is set to “true”, the session variable *<XS\_APPLICATIONUSER\>* must be set, too.



</td>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

IN



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

The key to be deleted within the target secure store \(`STORE_NAME`\)



</td>
</tr>
</table>

**Related Information**  


[Maintain Values in the SAP HANA Secure Store](maintain-values-in-the-sap-hana-secure-store-8a82c9e.md "Insert entries into (and retrieve and remove entries from) the SAP HANA Secure Store.")

[SAP HANA Cloud Deployment-Infrastructure Services](../70-HANA-Cloud-DB-Dev-App-Services/sap-hana-cloud-deployment-infrastructure-services-ebf0aa2.md "The SAP HANA Cloud Deployment Infrastructure service (HDI) is the central infrastructure component for application-container management.")

