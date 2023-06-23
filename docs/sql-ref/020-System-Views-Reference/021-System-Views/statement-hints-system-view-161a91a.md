<!-- loio161a91a544a442a4b66da674a80d98e0 -->

# STATEMENT\_HINTS System View

Provides information about statement hints, including when they were last enabled and/or disabled and by whom.



<a name="loio161a91a544a442a4b66da674a80d98e0___t_a_b_l_e_s_1struct_TABLES"/>

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

STATEMENT\_STRING



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the statement string.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the MD5 hash value for the STATEMENT\_STRING column.



</td>
</tr>
<tr>
<td valign="top">

HINT\_STRING



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the hint string.



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_HINT\_STRING



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the system hint string that conflicts with the existing user-defined hint string \(if a statement has both a user-defined hint and a system hint associated with it, then only the user-defined hint is effective\).



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

Displays whether the hint is enabled. Possible values: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ENABLE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp for when the hint was last enabled.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ENABLE\_USER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user who enabled the hint.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp for when the hint was last disabled.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_USER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user who disabled the hint.



</td>
</tr>
<tr>
<td valign="top">

IS\_OVERRIDE



</td>
<td valign="top">

NVARFCHAR\(5\)



</td>
<td valign="top">

Specifies TRUE if an override is specified for the target query \(e.g., ALTER SYSTEM ADD STATEMENT HINT.. OVERRIDE...\).



</td>
</tr>
<tr>
<td valign="top">

COMMENTS



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Specifies comments configured for a statement hint \(e.g., ALTER SYSTEM ADD STATEMENT HINT.. COMMENT *<comment\>*..\)



</td>
</tr>
</table>

**Related Information**  


[HINTS System View](hints-system-view-f55ce8e.md "Provides all available hints to be used in WITH HINT clauses.")

[HINT Details](../../010-SQL-Reference/012-SQL-Statements/hint-details-4ba9edc.md "The SQL Optimizer usually determines the access path (for example, index search versus table scan) on the basis of the costs (Cost-Based Optimizer). You can override the SQL Optimizer choice by explicitly specifying hints in the query that enforces a certain access path.")

[ALTER SYSTEM \{ADD | ALTER | REMOVE\} STATEMENT HINT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-add-alter-remove-statement-hint-statement-system-management-1ec23ef.md "Adds, alters, or removes statement hints from the system to a specified query or statement hash.")

