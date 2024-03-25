<!-- loiod076e2b58332452c878cf46ab2d56cdc -->

# CERTIFICATES System View

Provides information about certificates usable in PSEs.



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

CERTIFICATE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the unique name of the certificate.

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

Displays the unique identification of the certificate.

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

Displays the distinguished name of the X.509 certificate subject.

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

COMMENT

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the comment entered to describe the certificate.

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

KEY\_USAGE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the comma-separated list of key usage strings as specified in RFC 5280.

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

VERSION

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the version of the certificate format.

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



<a name="loiod076e2b58332452c878cf46ab2d56cdc__section_bbs_ppd_tfb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

For information on the permissions required to use this view, see *SQL Statements and Authorization for Certificate Management \(Reference\)*.

**Related Information**  


[PSE\_CERTIFICATES System View](pse-certificates-system-view-0184e53.md "Provides information about certificates used in PSEs.")

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

