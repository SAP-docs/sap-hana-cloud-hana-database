<!-- loio388378c0aa6b49dd88e9ee2187705f07 -->

# M\_EFFECTIVE\_PASSWORD\_POLICY System View

Provides information about password policy parameters for database users.



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

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user that this password policy is valid for.

</td>
</tr>
<tr>
<td valign="top">

PROPERTY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the password policy parameter.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the value of the password policy parameter.

</td>
</tr>
</table>



<a name="loio388378c0aa6b49dd88e9ee2187705f07__section_u2w_qdk_h2b"/>

## Additional Information

This view requires an equal predicate on USER\_NAME.

**Related Information**  


[M\_PASSWORD\_POLICY System View](m-password-policy-system-view-20b6e99.md "Defines effective password policy settings.")

[Password Policy Configuration Options](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/61662e3032ad4f8dbdb5063a21a7d706.html "The password policy of the database is defined by parameters in the password policy section of the indexserver.ini configuration file. The initial password policy of a user group is a copy of the database password policy.") :arrow_upper_right:

[CREATE USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md "Creates a usergroup.")

[ALTER USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-usergroup-statement-access-control-aa94ca8.md "Alters a usergroup.")

[GENERATE\_PASSWORD Function \(Security\)](../../010-SQL-Reference/011-SQL-Functions/generate-password-function-security-5157398.md "Generates a password.")

[CREATE USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-user-statement-access-control-20d5ddb.md "Creates a new database user.")

[ALTER USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-user-statement-access-control-20d3459.md "Modifies the database user.")

[DROP USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-user-statement-access-control-20d8d33.md "Deletes a database user.")

