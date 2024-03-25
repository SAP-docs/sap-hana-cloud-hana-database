<!-- loio89a066058d3f4e7f873216c6050181de -->

# WORKLOAD\_MAPPINGS System View

Provides information about available workload mappings.



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

WORKLOAD\_MAPPING\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the workload mapping name.

</td>
</tr>
<tr>
<td valign="top">

WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the workload class name.

</td>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name.

</td>
</tr>
<tr>
<td valign="top">

USERGROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user group.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the session variable APPLICATIONUSER.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wildcard character that is allowed in the user name.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the session variable APPLICATION.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wildcard character that is used in APPLICATION\_NAME.

</td>
</tr>
<tr>
<td valign="top">

CLIENT

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the session variable CLIENT.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wildcard character that is used in CLIENT.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the application component.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_COMPONENT\_NAME\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wildcard character that is used in APPLICATION\_COMPONENT\_NAME.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_COMPONENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the type of application component.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_COMPONENT\_TYPE\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wildcard character that is used in APPLICATION\_COMPONENT\_TYPE.

</td>
</tr>
<tr>
<td valign="top">

XS\_APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name assigned to the session variable XS\_APPLICATIONUSER.

</td>
</tr>
<tr>
<td valign="top">

XS\_APPLICATION\_USER\_NAME\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wildcard character that is used for the session variable XS\_APPLICATIONUSER.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_TENANT\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the session variable of the application tenant.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_TENANT\_NAME\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wild card of the application tenant.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the APPLICATIONSOURCE variable.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE\_WILDCARD

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the wild card of the APPLICATIONSOURCE variable.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the schema.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object.

</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the workload class is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the workload mapping is valid or not. This value is FALSE when its base object is changed or dropped: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio89a066058d3f4e7f873216c6050181de__section_ebc_1c1_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/create-workload-mapping-statement-workload-management-996978a.md "Defines workload mappings.")

[M\_WORKLOAD System View](../022-Monitoring-Views/m-workload-system-view-20cb5a7.md "Provides information about the database workload collected every minute.")

[WORKLOAD\_CLASSES System View](workload-classes-system-view-d520e47.md "Provides information about available workload classes.")

[Managing Workload with Workload Classes](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/5066181717df4110931271d1efd84cbc.html "You can manage workload in SAP HANA by creating workload classes and workload class mappings. Appropriate workload parameters are then dynamically applied to each client session.") :arrow_upper_right:

