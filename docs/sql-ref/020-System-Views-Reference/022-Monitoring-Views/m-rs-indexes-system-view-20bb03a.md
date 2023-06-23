<!-- loio20bb03af751910149db9bb524dae0b0f -->

# M\_RS\_INDEXES System View

Provides the statistics for B-tree and CPB-tree indexes.



<a name="loio20bb03af751910149db9bb524dae0b0f___m__r_s__i_n_d_e_x_e_s_1struct_M_RS_INDEXES"/>

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

Displays the internal port number.



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

INDEX\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the index name.



</td>
</tr>
<tr>
<td valign="top">

KEY\_TYPE



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the key type \(data or composite\).



</td>
</tr>
<tr>
<td valign="top">

INDEX\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the index status: VALID, INVALID, or UNUSABLE.



</td>
</tr>
<tr>
<td valign="top">

TREE\_HEIGHT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the B-tree level.



</td>
</tr>
<tr>
<td valign="top">

LEAF\_NODE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of leaf nodes.



</td>
</tr>
<tr>
<td valign="top">

NONLEAF\_NODE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of intermediate nodes.



</td>
</tr>
<tr>
<td valign="top">

NODE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the node size in bytes.



</td>
</tr>
<tr>
<td valign="top">

FANOUT



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the index fan-out.



</td>
</tr>
<tr>
<td valign="top">

BULKLOAD\_FACTOR



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the fill factor for creating or recovering indexes.



</td>
</tr>
<tr>
<td valign="top">

INDEX\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory index size \(number of nodes \* node size\) in bytes.



</td>
</tr>
<tr>
<td valign="top">

ENTRY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of indexed records.



</td>
</tr>
<tr>
<td valign="top">

FIXED\_LEAF\_NODE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of fixed leaf nodes. FIXED means that the key lengths of all entries in the node have the same value.



</td>
</tr>
<tr>
<td valign="top">

FIXED\_NONLEAF\_NODE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of fixed non-leaf nodes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_LEAF\_OFFSET\_SIZE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the average offset size of leaf nodes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_NONLEAF\_OFFSET\_SIZE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the average offset size of non-leaf nodes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_LEAF\_POINTER\_SIZE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the average pointer size of leaf nodes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_NONLEAF\_POINTER\_SIZE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the average pointer size of non-leaf nodes.



</td>
</tr>
<tr>
<td valign="top">

LEAF\_PARTIAL\_KEY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the partial key length of the leaf node.



</td>
</tr>
<tr>
<td valign="top">

NONLEAF\_PARTIAL\_KEY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the partial key length of the non-leaf node.



</td>
</tr>
<tr>
<td valign="top">

INDEX\_UTILIZATION



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the index utilization \(num\_entries / max\_entries\).



</td>
</tr>
<tr>
<td valign="top">

IS\_UNIQUE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays the whether the index is unique: TRUE or FALSE.



</td>
</tr>
<tr>
<td valign="top">

SEARCH\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of search operations.



</td>
</tr>
<tr>
<td valign="top">

DISTINCT\_KEY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of distinct keys.



</td>
</tr>
<tr>
<td valign="top">

KEY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of keys.



</td>
</tr>
<tr>
<td valign="top">

ELIMINATED\_DUPLICATE\_LEAF\_NODE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of leaf nodes whose duplicate keys are eliminated.



</td>
</tr>
<tr>
<td valign="top">

UNUSED\_LEAF\_SLOTS\_PER\_NODE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the number of unused slots per leaf node.



</td>
</tr>
</table>

**Related Information**  


[M\_RS\_MEMORY System View](m-rs-memory-system-view-20bb47a.md "Provides RS memory statistics.")

[M\_RS\_TABLES System View](m-rs-tables-system-view-20bbc60.md "Provides information about row tables, including detailed table sizes and record count.")

[M\_RS\_TABLE\_VERSION\_STATISTICS System View](m-rs-table-version-statistics-system-view-20bb882.md "Provides information on row table versions: detailed version counts and used sizes.")

[INDEXES System View](../021-System-Views/indexes-system-view-20a7044.md "Provides information about indexes on tables.")

[CREATE INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-index-statement-data-definition-20d44b4.md "Creates an index on a table column.")

[ALTER INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-index-statement-data-definition-20d014b.md "Alters an index.")

[RENAME INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-index-statement-data-definition-20fb6e1.md "Changes the name of an index.")

[DROP INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-index-statement-data-definition-20d6f4e.md "Removes an index.")

