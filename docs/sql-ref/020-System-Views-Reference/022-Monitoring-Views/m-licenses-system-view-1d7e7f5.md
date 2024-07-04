<!-- loio1d7e7f52f6574a238c137e17b0840673 -->

# M\_LICENSES System View

Provides information on all of the licenses \(if any\) that are installed on this system.



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

HARDWARE\_KEY

</td>
<td valign="top">

NVARCHAR\(11\)

</td>
<td valign="top">

Displays the hardware key of the SAP HANA installation.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_ID

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the system identifier \(SID\).

</td>
</tr>
<tr>
<td valign="top">

INSTALL\_NO

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays the installation number.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_NO

</td>
<td valign="top">

NVARCHAR\(18\)

</td>
<td valign="top">

Displays the system number.

</td>
</tr>
<tr>
<td valign="top">

GLAS\_APPLICATION\_ID

</td>
<td valign="top">

NVARCHAR\(6\)

</td>
<td valign="top">

Displays the license ID for the software product.

</td>
</tr>
<tr>
<td valign="top">

PRODUCT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the licensed software product, for example, SAP HANA.

</td>
</tr>
<tr>
<td valign="top">

PRODUCT\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the description of the licensed software product.

</td>
</tr>
<tr>
<td valign="top">

FIRST\_INSTALLATION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the date of the first installation of the license.

</td>
</tr>
<tr>
<td valign="top">

START\_DATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start date of the validity period of the license.

</td>
</tr>
<tr>
<td valign="top">

EXPIRATION\_DATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the expiration date of the validity period of the license.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SUCCESSFUL\_CHECK

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the latest date on which the license was successfully checked and found valid.

</td>
</tr>
<tr>
<td valign="top">

PERMANENT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays TRUE if the license is permanent and FALSE if the license is temporary.

</td>
</tr>
<tr>
<td valign="top">

VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the license is valid or not: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LOCKED\_DOWN

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the system is locked down due to license status: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_DATABASE\_LOCAL

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the license is a local database local license: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio1d7e7f52f6574a238c137e17b0840673__section_p4y_311_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_LICENSE System View](m-license-system-view-20b2007.md "Provides information on the currently valid license for the SAP HANA database that is installed on this system.")

