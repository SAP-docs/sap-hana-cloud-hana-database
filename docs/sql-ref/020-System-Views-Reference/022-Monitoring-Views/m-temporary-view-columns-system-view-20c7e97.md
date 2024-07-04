<!-- loio20c7e97575191014bc53f369ada03acb -->

# M\_TEMPORARY\_VIEW\_COLUMNS System View

Provides information about temporary view columns.



<a name="loio20c7e97575191014bc53f369ada03acb___m__t_e_m_p_o_r_a_r_y__v_i_e_w__c_o_l_u_m_n_s_1struct_M_TEMPORARY_VIEW_COLUMNS"/>

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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

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

Displays the view name.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the view.

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

Displays the view column name.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ordinal position of the view column.

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

Displays the SQL data type ID of the column.

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

Displays the SQL data type name of the column.

</td>
</tr>
<tr>
<td valign="top">

OFFSET

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the offset of the column in a record.

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

Displays the number of:

-   Characters for char types.
-   Max digits for numeric types.
-   Characters for datetime types.
-   Bytes for LOB types.



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

Displays the maximum number of digits to the right of the decimal point: TIME or TIMESTAMP. The decimal digits are defined as the number of digits to the right of the decimal point in the second's component of the data.

</td>
</tr>
<tr>
<td valign="top">

IS\_NULLABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is allowed to accept null value: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the default value in bytes.

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

Displays the description for this column.

</td>
</tr>
<tr>
<td valign="top">

DDIC\_DATA\_TYPE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the DDIC data type ID.

</td>
</tr>
<tr>
<td valign="top">

DDIC\_DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the DDIC data type name.

</td>
</tr>
<tr>
<td valign="top">

COMPRESSION\_TYPE

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays the type of compression: DEFAULT, PREFIXED, SPARSE, CLUSTERED, INDIRECT, or RLE.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_TYPE

</td>
<td valign="top">

NVARCHAR\(4\)

</td>
<td valign="top">

Displays the type of index: NONE/FULL.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the column.

</td>
</tr>
<tr>
<td valign="top">

PRELOAD

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is preloaded: TRUE/FALSE.

</td>
</tr>
</table>

**Related Information**  


[M\_TEMPORARY\_VIEWS System View](m-temporary-views-system-view-20c80e2.md "Displays temporary views.")

[M\_TEMPORARY\_TABLES System View](m-temporary-tables-system-view-20c7c6c.md "Provides information about temporary tables.")

[M\_TEMPORARY\_OBJECT\_DEPENDENCIES System View](m-temporary-object-dependencies-system-view-20c786a.md "Provides information about temporary object dependencies for transient objects.")

[M\_TEMPORARY\_JOIN\_CONSTRAINTS System View](m-temporary-join-constraints-system-view-d21b187.md "Provides information about temporary join constraints.")

[Handling Temporary Data](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/cffa9243511a4858882de2aa398a4899.html "") :arrow_upper_right:

