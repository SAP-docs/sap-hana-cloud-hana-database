<!-- loiobded95abb4ca4060a0cdd832acdf0ef0 -->

# PSE\_PUBLIC\_KEYS System View

Provides information about all public keys in a PSE store.



<a name="loiobded95abb4ca4060a0cdd832acdf0ef0__section_pnq_ynd_tfb"/>

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

Displays the name of the PSE.

</td>
</tr>
<tr>
<td valign="top">

PUBLIC\_KEY\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the unique name of the public key.

</td>
</tr>
</table>



<a name="loiobded95abb4ca4060a0cdd832acdf0ef0__section_bbs_ppd_tfb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

For information on the permissions required to use this view, see *SQL Statements and Authorization for Certificate Management \(Reference\)*.

**Related Information**  


[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

[PUBLIC\_KEYS System View](public-keys-system-view-4924523.md "Provides information about all public keys.")

