<!-- loio0184e531d3854f2c8b58ffab49763ddb -->

# PSE\_CERTIFICATES System View

Provides information about certificates used in PSEs.



## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

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

Displays the name of the PSE.

</td>
</tr>
<tr>
<td valign="top">

CERTIFICATE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique ID of the certificate.

</td>
</tr>
<tr>
<td valign="top">

SUBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the subject of the X.509 certificate.

</td>
</tr>
<tr>
<td valign="top">

ISSUER\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the issuer of the X.509 certificate.

</td>
</tr>
<tr>
<td valign="top">

VALID\_FROM

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time of certificate's validity.

</td>
</tr>
<tr>
<td valign="top">

VALID\_UNTIL

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the end time of certificate's validity.

</td>
</tr>
<tr>
<td valign="top">

CERTIFICATE\_USAGE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the certificate usage: OWN, CHAIN, or TRUST.

</td>
</tr>
<tr>
<td valign="top">

CERTIFICATE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the unique name of the certificate.

</td>
</tr>
</table>



<a name="loio0184e531d3854f2c8b58ffab49763ddb__section_bbs_ppd_tfb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

For information on the permissions required to use this view, see *SQL Statements and Authorization for Certificate Management \(Reference\)*.

**Related Information**  


[PSES System View](pses-system-view-6d9713d.md "Provides information about personal security environments (PSE).")

[PSE\_PURPOSE\_OBJECTS System View](pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[Certificate Management](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/1e6042c4402545f7a0574f7bc91fab25.html "SAP HANA uses public-key certificates as the basis for several user authentication mechanisms, and for securing internal and external communication channels. Certificates are stored and managed directly in the SAP HANA database.") :arrow_upper_right:

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

