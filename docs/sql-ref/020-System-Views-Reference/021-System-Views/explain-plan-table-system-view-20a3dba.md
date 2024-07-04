<!-- loio20a3dbac75191014b400b72d0f02eabe -->

# EXPLAIN\_PLAN\_TABLE System View

Provides information about SQL query plan explanation results.



<a name="loio20a3dbac75191014b400b72d0f02eabe___e_x_p_l_a_i_n__p_l_a_n__t_a_b_l_e_1struct_EXPLAIN_PLAN_TABLE"/>

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

STATEMENT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the string specified as STATEMENT\_NAME when executing the EXPLAIN PLAN command. This is used to distinguish plans from each other when there are multiple plans in EXPLAIN\_PLAN\_TABLE view.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays a column engine or row engine operator. See the Additional Information section within this topic for more information about the possible values in this column.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_DETAILS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays details of an operator including predicates and expressions used by the operator.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_PROPERTIES.

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the internal properties of an operator.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_ENGINE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the execution engine where the plan operator is executed: COLUMN, HEX, ROW, or SQLScript.

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database name that the object belongs to.

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

Displays the schema name the dependent object belongs to.

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

Displays the name of the database tables and views accessed by an operator.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the table stored type: COLUMN or ROW.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_SIZE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the estimated input row count of an operator. This is available only for operators accessing tables and views directly.

</td>
</tr>
<tr>
<td valign="top">

OUTPUT\_SIZE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the estimated output row count of an operator.

</td>
</tr>
<tr>
<td valign="top">

SUBTREE\_COST

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the estimated cost based on estimated cardinality information. This value is used for the cost-based optimizer to choose the best plan. The value can also be a possible indicator to compare two different plans for the same query; the smaller the subtree cost, typically the better the performance.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the unique ID of an operator. IDs are integers starting from 1.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_OPERATOR\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the operator ID of the parent of an operator. The shape of a query plan is a tree and the topology of the tree can be reconstructed using OPERATOR\_ID and PARENT\_OPERATOR\_ID. The PARENT\_OPERATOR\_ID of the root operator appears as NULL.

</td>
</tr>
<tr>
<td valign="top">

LEVEL

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the level from the root operator. The level of the root operator is 1, the level of a child of the root operator is 2, and so on. This can be utilized for output indentation.

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

Displays the position in the parent operator. The position of the first child is 1, the position of the second child is 2, and so on.

</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the host where the plan operator is generated.

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

Displays the port where the plan operator is generated.

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the date and time when the EXPLAIN PLAN command was executed.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID.

</td>
</tr>
</table>



<a name="loio20a3dbac75191014b400b72d0f02eabe__section_lcj_245_4zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20a3dbac75191014b400b72d0f02eabe___e_x_p_l_a_i_n__p_l_a_n__t_a_b_l_e_1fulldesc_EXPLAIN_PLAN_TABLE"/>

## Additional Information

The OPERATOR\_NAME column can contain **column engine** and **row engine** operators, as shown in the following tables.

Column engine operators:


<table>
<tr>
<th valign="top">

Operator Name

</th>
<th valign="top">

Description.

</th>
</tr>
<tr>
<td valign="top">

COLUMN SEARCH

</td>
<td valign="top">

Displays the starting position of column engine operators. OPERATOR\_DETAILS lists the projected columns.

</td>
</tr>
<tr>
<td valign="top">

LIMIT

</td>
<td valign="top">

Displays the operator for limiting the number of output rows.

</td>
</tr>
<tr>
<td valign="top">

ORDER BY

</td>
<td valign="top">

Displays the operator for sorting output rows.

</td>
</tr>
<tr>
<td valign="top">

HAVING

</td>
<td valign="top">

Displays the operator for filtering with predicates on top of grouping and aggregation.

</td>
</tr>
<tr>
<td valign="top">

GROUP BY

</td>
<td valign="top">

Displays the operator for grouping and aggregation.

</td>
</tr>
<tr>
<td valign="top">

DISTINCT

</td>
<td valign="top">

Displays the operator for duplicate elimination.

</td>
</tr>
<tr>
<td valign="top">

FILTER

</td>
<td valign="top">

Displays the operator for filtering with predicates.

</td>
</tr>
<tr>
<td valign="top">

JOIN

</td>
<td valign="top">

Displays the operator for joining input relations.

</td>
</tr>
<tr>
<td valign="top">

COLUMN TABLE

</td>
<td valign="top">

Displays information about accessed column tables.

</td>
</tr>
<tr>
<td valign="top">

MULTIPROVIDER

</td>
<td valign="top">

Displays the operator for producing union-all of multiple results having the same grouping and aggregation.

</td>
</tr>
</table>

Row engine operators:


<table>
<tr>
<th valign="top">

Operator Name

</th>
<th valign="top">

Description.

</th>
</tr>
<tr>
<td valign="top">

ROW SEARCH

</td>
<td valign="top">

Displays the starting position of row engine operators. OPERATOR\_DETAILS lists the projected columns.

</td>
</tr>
<tr>
<td valign="top">

LIMIT

</td>
<td valign="top">

Displays the operator for limiting the number of output rows.

</td>
</tr>
<tr>
<td valign="top">

ORDER BY

</td>
<td valign="top">

Displays the operator for sorting output rows.

</td>
</tr>
<tr>
<td valign="top">

HAVING

</td>
<td valign="top">

Displays the operator for filtering with predicates on top of grouping and aggregation.

</td>
</tr>
<tr>
<td valign="top">

GROUP BY

</td>
<td valign="top">

Displays the operator for grouping and aggregation.

</td>
</tr>
<tr>
<td valign="top">

MERGE AGGREGATION

</td>
<td valign="top">

Displays the operator for merging the results of multiple parallel grouping and aggregations.

</td>
</tr>
<tr>
<td valign="top">

DISTINCT

</td>
<td valign="top">

Displays the operator for duplicate elimination.

</td>
</tr>
<tr>
<td valign="top">

FILTER

</td>
<td valign="top">

Displays the operator for filtering with predicates.

</td>
</tr>
<tr>
<td valign="top">

UNION ALL

</td>
<td valign="top">

Displays the operator for producing union-all of input relations.

</td>
</tr>
<tr>
<td valign="top">

MATERIALIZED UNION ALL

</td>
<td valign="top">

Displays the operator for producing union-all of input relations with intermediate result materialization.

</td>
</tr>
<tr>
<td valign="top">

BTREE INDEX JOIN

</td>
<td valign="top">

Displays the operator for joining input relations through B-tree index searches. A join type suffix can be added, for example, B-tree index join for left outer join is shown as BTREE INDEX JOIN \(LEFT OUTER\). A join without a join type suffix means an inner join.

</td>
</tr>
<tr>
<td valign="top">

CPBTREE INDEX JOIN

</td>
<td valign="top">

Displays the operator for joining input relations through CPB-tree index searches. A join type suffix can be added.

</td>
</tr>
<tr>
<td valign="top">

HASH JOIN

</td>
<td valign="top">

Displays the operator for joining input relations through probing hash table built on the fly. A join type suffix can be added.

</td>
</tr>
<tr>
<td valign="top">

NESTED LOOP JOIN

</td>
<td valign="top">

Displays the operator for joining input relations through nested looping. A join type suffix can be added.

</td>
</tr>
<tr>
<td valign="top">

MIXED INVERTED INDEX JOIN

</td>
<td valign="top">

Displays the operator for joining an input relation of row store format with a column table without format conversion using an inverted index of the column table. A join type suffix can be added.

</td>
</tr>
<tr>
<td valign="top">

BTREE INDEX SEARCH

</td>
<td valign="top">

Displays the table access through B-tree index search.

</td>
</tr>
<tr>
<td valign="top">

CPBTREE INDEX SEARCH

</td>
<td valign="top">

Displays the table access through CPB-tree index search.

</td>
</tr>
<tr>
<td valign="top">

TABLE SCAN

</td>
<td valign="top">

Displays the table access through scanning.

</td>
</tr>
<tr>
<td valign="top">

AGGR TABLE

</td>
<td valign="top">

Displays the operator for aggregating base table directly.

</td>
</tr>
<tr>
<td valign="top">

MONITOR SEARCH

</td>
<td valign="top">

Displays the monitoring view access through a search.

</td>
</tr>
<tr>
<td valign="top">

MONITOR SCAN

</td>
<td valign="top">

Displays the monitoring view access through scanning.

</td>
</tr>
</table>

**Related Information**  


[EXPLAIN PLAN Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/explain-plan-statement-data-manipulation-20d9ec5.md "Evaluates the execution plan that the database follows when executing an SQL statement.")

[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

[EXPLAIN PLAN for Call](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/7aabea5031134d2192f7022bc390fce6.html "") :arrow_upper_right:

[EXPLAIN PLAN for Table User-Defined Functions](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/de08addfcf2242c9a6acea09620aa889.html "") :arrow_upper_right:

