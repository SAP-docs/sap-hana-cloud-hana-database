<!-- loio7e667ef7ff2d49d7a7a9d4aec27c4b41 -->

# M\_CUSTOMIZABLE\_FUNCTIONALITIES System View

Provides information about the enablement status of restricted features in databases. The full content of this view is only accessible from the system database.



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

NAME



</td>
<td valign="top">

NVARCHAR \(64\)



</td>
<td valign="top">

Displays the customizable functionality name.



</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the customizable functionality description.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED



</td>
<td valign="top">

NVARCHAR \(5\)



</td>
<td valign="top">

Indicates whether the customizable functionality is enabled: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[M\_FEATURES System View](m-features-system-view-20afe0e.md "Provides information about all supported features.")

[M\_FEATURE\_USAGE System View](m-feature-usage-system-view-96491c8.md "Provides detailed feature usage statistics.")

