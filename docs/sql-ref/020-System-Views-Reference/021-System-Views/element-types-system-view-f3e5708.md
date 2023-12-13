<!-- loiof3e5708b6f5b1014a1289f6ed0d907b6 -->

# ELEMENT\_TYPES System View

Provides information about available multivalued types.



<a name="loiof3e5708b6f5b1014a1289f6ed0d907b6___e_l_e_m_e_n_t__t_y_p_e_s_1struct_ELEMENT_TYPES"/>

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

Displays the name of the schema containing the object that defines or uses the collection type.

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

Displays the name of the table, view, or procedure that defines or uses the collection type.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the identifier of the table, view, or procedure that defines or uses the collection type.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the object type: TABLE, VIEW, or FUNCTION.

</td>
</tr>
<tr>
<td valign="top">

ELEMENT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the table or view column or procedure parameter.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_ID

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the identifier of the element type.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the name of the element type.

</td>
</tr>
<tr>
<td valign="top">

LENGTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the length for a character string type or the precision for a numeric type in bytes.

</td>
</tr>
<tr>
<td valign="top">

SCALE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the scale for a numeric type.

</td>
</tr>
<tr>
<td valign="top">

MIN\_CARDINALITY

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the lower bound of the array.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CARDINALITY

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the upper bound of the array.

</td>
</tr>
<tr>
<td valign="top">

ALLOW\_DUPLICATES

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates if duplicates are allowed within one column: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loiof3e5708b6f5b1014a1289f6ed0d907b6__section_c5t_mhr_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Multi-valued Data Types](../../010-SQL-Reference/multi-valued-data-types-cae8b00.md "Multi-valued types are used to store collections of values sharing the same data type.")

[CREATE TYPE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/create-type-statement-procedural-20d5c1e.md "Creates a user-defined type")

[DROP TYPE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/drop-type-statement-procedural-20d83be.md "Removes a user-defined table type.")

