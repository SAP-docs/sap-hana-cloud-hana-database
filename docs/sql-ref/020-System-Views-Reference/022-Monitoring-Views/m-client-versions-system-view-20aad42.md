<!-- loio20aad425751910149677cd293a8379c2 -->

# M\_CLIENT\_VERSIONS System View

Provides versions of all supported client applications.



<a name="loio20aad425751910149677cd293a8379c2___m__c_l_i_e_n_t__v_e_r_s_i_o_n_s_1struct_M_CLIENT_VERSIONS"/>

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

CLIENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the type of client, for example, ABAP\_FDA or BI Modeler.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_RELEASE\_ID

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the technical release ID.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_RELEASE\_DESC

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the human readable release description.

</td>
</tr>
<tr>
<td valign="top">

MIN\_VERSION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the lowest supported protocol version.

</td>
</tr>
<tr>
<td valign="top">

MAX\_VERSION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the highest supported protocol version.

</td>
</tr>
</table>

