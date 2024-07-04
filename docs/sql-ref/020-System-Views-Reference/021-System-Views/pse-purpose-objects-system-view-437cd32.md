<!-- loio437cd32f9773425ba4e0facb7cb0a09c -->

# PSE\_PURPOSE\_OBJECTS System View

Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.



<a name="loio437cd32f9773425ba4e0facb7cb0a09c__section_pnq_ynd_tfb"/>

## Structure


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

PSE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the PSE store.

</td>
</tr>
<tr>
<td valign="top">

PURPOSE

</td>
<td valign="top">

NVARCHAR\(24\)

</td>
<td valign="top">

Displays the purpose of the PSE store.

</td>
</tr>
<tr>
<td valign="top">

PURPOSE\_OBJECT

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

For JWT or SAML purposes, displays the name of the assigned provider. For the SSL purpose, this is the assigned host name.

</td>
</tr>
<tr>
<td valign="top">

PURPOSE\_OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

The type of purpose. Valid entries are:

-   SAML PROVIDER
-   REMOTE SOURCE
-   HOST
-   MANAGED PSE



</td>
</tr>
<tr>
<td valign="top">

ADD\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time the PSE purpose object was added to the PSE.

</td>
</tr>
</table>



<a name="loio437cd32f9773425ba4e0facb7cb0a09c__section_rtw_w4d_tfb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view also requires the TRUST ADMIN system privilege to see all entries in the PSE\_PURPOSE\_OBJECTS system view.No additional privilege is required to see those entries for which you have the REFERENCES or ALTER privilege on the PSE object.

For information on the permissions required to use this view, see *SQL Statements and Authorization for Certificate Management \(Reference\)*.



<a name="loio437cd32f9773425ba4e0facb7cb0a09c__section_bbs_ppd_tfb"/>

## Additional Information

One PSE may have multiple lines, one line per assigned provider or host. All PSEs are shown, including those with and without a purpose and those with and without a purpose object assigned.

**Related Information**  


[PSES System View](pses-system-view-6d9713d.md "Provides information about personal security environments (PSE).")

[PSE\_CERTIFICATES System View](pse-certificates-system-view-0184e53.md "Provides information about certificates used in PSEs.")

[CREATE PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/create-pse-statement-system-management-4d80bf6.md "Creates a personal security environment (PSE).")

[SET PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE, which is the type of trust validation for the PSE to use.")

[UNSET PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/unset-pse-statement-system-management-4082553.md "Remove the assigned purpose for a PSE along with any assigned objects.")

[ALTER PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[DROP PSE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-pse-statement-system-management-25d6795.md "Drops a PSE.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[Certificate Management](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/1e6042c4402545f7a0574f7bc91fab25.html "SAP HANA uses public-key certificates as the basis for several user authentication mechanisms, and for securing internal and external communication channels. Certificates are stored and managed directly in the SAP HANA database.") :arrow_upper_right:

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

