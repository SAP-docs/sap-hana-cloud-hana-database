<!-- loio20ccc0a175191014901b88e6bc175c44 -->

# REFERENTIAL\_CONSTRAINTS System View

Provides information about referential constraints.



<a name="loio20ccc0a175191014901b88e6bc175c44___r_e_f_e_r_e_n_t_i_a_l__c_o_n_s_t_r_a_i_n_t_s_1struct_REFERENTIAL_CONSTRAINTS"/>

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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the column position in this constraint.

</td>
</tr>
<tr>
<td valign="top">

CONSTRAINT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the constraint name.

</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the table referenced by this constraint.

</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the table referenced by this constraint.

</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column referenced by this column.

</td>
</tr>
<tr>
<td valign="top">

REFERENCED\_CONSTRAINT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the unique constraint referenced by this constraint.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_RULE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the update rule: CASCADE, SET NULL, SET DEFAULT, or RESTRICT.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_RULE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the delete rule: CASCADE, SET NULL, SET DEFAULT, or RESTRICT.

</td>
</tr>
<tr>
<td valign="top">

IS\_ENFORCED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not this constraint is enforced: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALIDATED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not this constraint is validated: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

CHECK\_TIME

</td>
<td valign="top">

STRING

</td>
<td valign="top">

Displays the time when the constraint is checked: INITIALLY\_IMMEDIATE/INITIALLY DEFERRED.

</td>
</tr>
</table>



<a name="loio20ccc0a175191014901b88e6bc175c44__section_jqt_gy4_dzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CONSTRAINTS System View](constraints-system-view-209f7cf.md "Provides information about defined constraints for tables.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[CS\_JOIN\_CONSTRAINTS System View](cs-join-constraints-system-view-20a06e5.md "Provides join constraints for column store join views.")

[SQL DML Statements on Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/226f2125b7ed4f4aabe731cfed029d7b.html "") :arrow_upper_right:

[Table Variable Type Definition](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/ea5065d06d14426799d879234d8e3e7b.html "") :arrow_upper_right:

