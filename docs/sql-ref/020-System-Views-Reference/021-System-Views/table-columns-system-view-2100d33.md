<!-- loio2100d33a75191014868bbcd89274199c -->

# TABLE\_COLUMNS System View

Provides information about available table columns.



<a name="loio2100d33a75191014868bbcd89274199c___t_a_b_l_e__c_o_l_u_m_n_s_1struct_TABLE_COLUMNS"/>

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

TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the table.

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

Displays the name of the column.

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

Indicates the ordinal position of the column in a record.

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

Displays the offset of the column in the record.

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

Indicates the number of chars for CHAR types, number of max digits for numeric types, number of chars for datetime types, and number of bytes for LOB types.

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

Indicates the numeric types: the maximum number of digits to the right of the decimal point; time, timestamp: the decimal digits are defined as the number of digits to the right of the decimal point in the second's component of the data.

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

Displays whether the column is allowed to accept null values: TRUE or FALSE.

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

Displays the default value of the column.

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

Indicates the type of compression: DEFAULT, PREFIXED, SPARSE, CLUSTERED, SPARSE, CLUSTERED, INDIRECT, RLE, and LINEAR RLE. The default value for the column is shown. The actual value can be checked in the system view M\_ CS\_COLUMNS. For row store columns, NONE is shown.

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

Indicates the type of index: NONE or FULL.

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

Displays if the column is preloaded: TRUE or FALSE. Preload information can be NULL in case of row storeor virtual columns.

</td>
</tr>
<tr>
<td valign="top">

GENERATED\_ALWAYS\_AS

</td>
<td valign="top">

NVARCHAR\(1000\)

</td>
<td valign="top">

Displays the expression of the column created by GENERATED... AS.

</td>
</tr>
<tr>
<td valign="top">

FUZZY\_SEARCH\_INDEX

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if the column has a fuzzy search index: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

FUZZY\_SEARCH\_MODE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the fuzzy search mode.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_THRESHOLD

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the memory threshold in bytes for LOB types.

</td>
</tr>
<tr>
<td valign="top">

LOAD\_UNIT

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the unit of column data loading: TABLE, COLUMN, PAGE, or DEFAULT.

</td>
</tr>
<tr>
<td valign="top">

GENERATION\_TYPE

</td>
<td valign="top">

NVARCHAR\(22\)

</td>
<td valign="top">

Displays ALWAYS AS if the column is generation column, ALWAYS AS IDENTITY, BY DEFAULT AS IDENTITY if the column is an identity column whose values are always generated or generated by default, and NULL otherwise.

For system-versioning columns, the value 'ALWAYS AS ROW START' indicates a column that was defined as GENERATED ALWAYS AS ROW START, while the value 'ALWAYS AS ROW END' indicates a column that was defined as GENERATED ALWAYS AS ROW END.

</td>
</tr>
<tr>
<td valign="top">

IS\_CACHABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is part of cached data: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_CACHE\_KEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is part of cache key: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

ROW\_ORDER\_POSITION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the position of the row in the table.

</td>
</tr>
<tr>
<td valign="top">

IS\_HIDDEN

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is hidden: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_MASKED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is masked: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

MASK\_EXPRESSION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the mask expression. See Permissions for further details.

</td>
</tr>
<tr>
<td valign="top">

CLIENTSIDE\_ENCRYPTION\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Internal use only.

</td>
</tr>
<tr>
<td valign="top">

CLIENTSIDE\_ENCRYPTION\_COLUMN\_KEY\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Internal use only.

</td>
</tr>
<tr>
<td valign="top">

CLIENTSIDE\_ENCRYPTION\_MODE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Internal use only.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the user-specified persistent memory preference: TRUE \(persistent memory is ON\), or FALSE \(persistent memory OFF\). If the user has not specified a persistent memory preference, or if the preference is set to the default, then the value is NULL.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_INDEXES

</td>
<td valign="top">

NVARCHAR \(1024\)

</td>
<td valign="top">

Displays a comma-separated list of user-specified logical NUMA node indexes for the table columns. For each column entry in this view there will be preferences \(if set\); otherwise, the value is NULL.

The elements of the list are either individual nodes indexes or ranges of index nodes, or a mixture of both. For example, the value ***0, 1 TO 3, 6*** indicates node indexes 0, 1, 2, 3, and 6.

</td>
</tr>
</table>



<a name="loio2100d33a75191014868bbcd89274199c__section_cyy_lxz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

The column MASK\_EXPRESSION is only visible to users who are the owner of the table or schema and have the SELECT METADATA privilege on the schema.

**Related Information**  


[TABLE\_COLUMNS\_ODBC System View](table-columns-odbc-system-view-210065d.md "Provides information about available table columns.")

[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[RENAME COLUMN Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-column-statement-data-definition-20fb2b8.md "Changes the name of a column.")

[Check the Compression of a Column Table](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bfbbf27bbb5710149299ee91cc769734.html "For column-store tables, you can check the type of compression applied to table columns.") :arrow_upper_right:

[Compress a Column Table Manually](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bfdd39c0bb571014b690889664aecc94.html "The SAP HANA database decides which columns in a column table to compress and which compression algorithm to apply for each column. It does this as part of the delta merge operation. It is normally not necessary that you interfere with this process. However, you can trigger compression manually.") :arrow_upper_right:

[Load/Unload a Column Table into/from Memory](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/c133165bbb57101493c5fb19b5b8607f.html "Under normal circumstances, the SAP HANA database manages the loading and unloading of tables into and from memory automatically, the aim being to keep all relevant data in memory. However, you can manually load and unload individual tables, as well as load table columns if necessary.") :arrow_upper_right:

