<!-- loio087f2a01433e4ccca3f707fd9e177f2d -->

# ROOT\_CERTIFICATES System View

Provides information about root certificates.



<a name="loio087f2a01433e4ccca3f707fd9e177f2d__section_iy4_5nw_njb"/>

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

HOST\_NAME

</td>
<td valign="top">

NVARCHAR

</td>
<td valign="top">

Internal use.

</td>
</tr>
<tr>
<td valign="top">

SUBJECT\_COMMON\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the common name of the X.509 certificate subject.

</td>
</tr>
<tr>
<td valign="top">

ISSUER\_COMMON\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the common name of the X.509 certificate issuer.

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

Displays the start time of a certificate's validity.

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

Displays the end time of a certificate's validity.

</td>
</tr>
<tr>
<td valign="top">

COMMENT

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the description for the certificate.

</td>
</tr>
<tr>
<td valign="top">

SUBJECT\_DISTINGUISHED\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the distinguished name of the X.509 certificate subject.

</td>
</tr>
<tr>
<td valign="top">

ISSUER\_DISTINGUISHED\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the distinguished name of the X.509 certificate issuer.

</td>
</tr>
<tr>
<td valign="top">

BASIC\_CONSTRAINTS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the basic constraints.

</td>
</tr>
<tr>
<td valign="top">

SUBJECT\_ALT\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the comma-separated list of alternative names of the X.509 certificate subject.

</td>
</tr>
<tr>
<td valign="top">

PUBLIC\_KEY\_ALGORITHM

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the public key algorithm.

</td>
</tr>
<tr>
<td valign="top">

PUBLIC\_KEY\_LENGTH

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the public key length.

</td>
</tr>
<tr>
<td valign="top">

SIGNATURE\_ALGORITHM

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the signature algorithm.

</td>
</tr>
<tr>
<td valign="top">

SERIAL\_NUMBER

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the serial number as assigned from the certificate issuer.

</td>
</tr>
<tr>
<td valign="top">

FINGERPRINT

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the hash of the entire certificate. It is used as a unique identifier in the certificate store.

</td>
</tr>
<tr>
<td valign="top">

CERTIFICATE

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the certificate as given during SQL.

</td>
</tr>
</table>



<a name="loio087f2a01433e4ccca3f707fd9e177f2d__section_wjj_kbp_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

