<!-- loioe9ec687ab91243b8a0f0f52a16b49c2d -->

# M\_ALL\_GROUP\_CONFIGURATIONS

View all HDI container-group configurations in the database.



The `_SYS_DI` monitoring view `M_ALL_GROUP_CONFIGURATIONS` shows all HDI container-group configuration keys in the database, which are visible to the user, for example, the container-group configuration parameter `enable_cross_container_access`, which is used to enable access to objects in other containers in the same HDI container group.

> ### Note:  
> The view is public

**M\_ALL\_GROUP\_CONFIGURATIONS**


<table>
<tr>
<th valign="top">

Name



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

CONTAINER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the container group



</td>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the container-group configuration key



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

The value for the specified container-group `KEY` 



</td>
</tr>
</table>

**Related Information**  


[M\_ALL\_CONTAINER\_CONFIGURATIONS](m-all-container-configurations-e68a6e7.md "View all HDI container configurations in the database.")

[M\_CONFIGURATION](../../20-HDI-Cloud-Content-Development/m-configuration-b2b6ed1.md "View information about the changes made to the configuration of an HDI container.")

