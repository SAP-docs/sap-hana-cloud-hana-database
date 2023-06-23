<!-- loioe68a6e7fe5dd4b76a4f919db1cc5ee33 -->

# M\_ALL\_CONTAINER\_CONFIGURATIONS

View all HDI container configurations in the database.



The `_SYS_DI` monitoring view `M_ALL_CONTAINER_CONFIGURATIONS` shows all HDI container configuration keys in the database, which are visible to the user. This view includes the container configuration keys \(for example, container-specific configuration parameters such as `messages. days_to_keep` or `make.validate_external_dependencies`\) and their corresponding values, which are stored for each HDI container and listed in the related container-specific `M_CONFIGURATION` view.

> ### Note:  
> The view is public

**M\_ALL\_CONTAINER\_CONFIGURATIONS**


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

The name of the container



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

The name of the container configuration key



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

The value for the specified `KEY` 



</td>
</tr>
</table>

**Related Information**  


[M\_ALL\_GROUP\_CONFIGURATIONS](m-all-group-configurations-e9ec687.md "View all HDI container-group configurations in the database.")

[M\_CONFIGURATION](../../20-HDI-Cloud-Content-Development/m-configuration-b2b6ed1.md "View information about the changes made to the configuration of an HDI container.")

