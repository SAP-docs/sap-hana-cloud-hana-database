<!-- loiod21ad20fd2951014ba93cfa9aa185a32 -->

# M\_TEMPORARY\_JOIN\_CONDITIONS System View

Provides information about temporary join conditions.



<a name="loiod21ad20fd2951014ba93cfa9aa185a32___m__t_e_m_p_o_r_a_r_y__j_o_i_n__c_o_n_d_i_t_i_o_n_s_1struct_M_TEMPORARY_JOIN_CONDITIONS"/>

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

VIEW\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the join view name.



</td>
</tr>
<tr>
<td valign="top">

JOIN\_CONDITION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the join condition name.



</td>
</tr>
<tr>
<td valign="top">

JOIN\_ORDER



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the join order number.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_SCHEMA\_NAME1



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of column1.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME1



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name of column1.



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME1



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of column1.



</td>
</tr>
<tr>
<td valign="top">

ALIAS\_NUMBER1



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the alias number of table name1.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_SCHEMA\_NAME2



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of column2.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME2



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name of column2.



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME2



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of column2.



</td>
</tr>
<tr>
<td valign="top">

ALIAS\_NUMBER2



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the alias number of table name2.



</td>
</tr>
<tr>
<td valign="top">

CONSTRAINTS



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the join constraint name.



</td>
</tr>
<tr>
<td valign="top">

JOIN\_TYPE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays the join type.



</td>
</tr>
<tr>
<td valign="top">

CARDINALITY



</td>
<td valign="top">

NVARCHAR\(3\)



</td>
<td valign="top">

Displays the join cardinality.



</td>
</tr>
</table>

**Related Information**  


[M\_TEMPORARY\_JOIN\_CONSTRAINTS System View](m-temporary-join-constraints-system-view-d21b187.md "Provides information about temporary join constraints.")

[ALTER SYSTEM CLEAR COLUMN JOIN DATA STATISTICS \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-column-join-data-statistics-system-management-9ac0859.md "Removes join data statistics from the SAP HANA database cache.")

