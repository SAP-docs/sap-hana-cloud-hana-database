<!-- loio209e4d3d75191014b419a2dc6e6a202a -->

# AUDIT\_POLICIES System View

Provides information about audit policies.



<a name="loio209e4d3d75191014b419a2dc6e6a202a___a_u_d_i_t__p_o_l_i_c_i_e_s_1struct_AUDIT_POLICIES"/>

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

AUDIT\_POLICY\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the audit policy name.

</td>
</tr>
<tr>
<td valign="top">

AUDIT\_POLICY\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the audit policy.

</td>
</tr>
<tr>
<td valign="top">

EVENT\_STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the status of events to be audited: SUCCESSFUL EVENTS, UNSUCCESSFUL EVENTS, ALL EVENTS.

</td>
</tr>
<tr>
<td valign="top">

EVENT\_LEVEL

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the level of events to be audited: EMERGENCY, CRITICAL, ALERT, WARNING, INFO.

</td>
</tr>
<tr>
<td valign="top">

IS\_AUDIT\_POLICY\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the audit policy is active: TRUE/ FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays whether an audit policy is valid. An audit policy can be invalid if the referenced user or object does not exist or an invalid combination of action and object is specified \(for example, EXECUTE on a table\). Possible values are TRUE/ FALSE.

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

Displays whether the policy was created locally on the current database and can be changed from within this database:TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

EVENT\_ACTION

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the action to be audited, such as SELECT or GRANT PRIVILEGE.

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

Displays the user whose actions are to be audited.

</td>
</tr>
<tr>
<td valign="top">

EXCEPT\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user whose actions are not to be audited.

</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the principal whose actions or whose members’ actions are to be audited.

</td>
</tr>
<tr>
<td valign="top">

EXCEPT\_PRINCIPAL\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the principal whose actions or whose members’ actions are not to be audited.

</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays whether the principal or except principal is USER or USERGROUP. When if the value of PRINCIPAL\_TYPE is USER, the columns PRINCIPAL\_NAME and EXCEPT\_PRINCIPAL\_NAME display the same values as the columns USER\_NAME and EXCEPT\_USER\_NAME, respectively.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of object to be audited, or INVALID if the object type was changed after the audit policy was created.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCHEMA

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema of object to be audited.

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

Displays the name of object to be audited.

</td>
</tr>
<tr>
<td valign="top">

TRAIL\_TYPE

</td>
<td valign="top">

NVARCHAR\(6\)

</td>
<td valign="top">

Displays the name of the audit trail where the audit entry is written.

</td>
</tr>
<tr>
<td valign="top">

RETENTION\_PERIOD

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of days the corresponding audit entries are retained.

</td>
</tr>
</table>



<a name="loio209e4d3d75191014b419a2dc6e6a202a__section_jxz_5fc_qhb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view also requires the CATALOG READ or AUDIT ADMIN system privilege.

**Related Information**  


[AUDIT\_LOG System View](audit-log-system-view-d1fe124.md "Provides information about audit records, with the exception of XSA-auditing.")

[CREATE AUDIT POLICY Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-audit-policy-statement-access-control-20d3d56.md "Creates an audit policy.")

[ALTER AUDIT POLICY Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-audit-policy-statement-access-control-20cfb7b.md "Enables or disables an audit policy, changes audit trail target types for an audit policy, and configures the retention period of the policy.")

[DROP AUDIT POLICY Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-audit-policy-statement-access-control-20d6324.md "Drops an audit policy.")

[Best Practices and Recommendations for Creating Audit Policies](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/35eb4e567d53456088755b8131b7ed1d.html "Best practices and recommendations to help you create audit policies") :arrow_upper_right:

