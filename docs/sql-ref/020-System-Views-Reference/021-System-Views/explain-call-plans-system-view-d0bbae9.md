<!-- loiod0bbae92c44b489db4b662bb6fed1909 -->

# EXPLAIN\_CALL\_PLANS System View

Provides information about the compiled plan of a given procedure.



<a name="loiod0bbae92c44b489db4b662bb6fed1909__section_f45_vrn_phb"/>

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

OPERATOR\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the name of logical operator.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement string or code \(llvm, expression, ce\) string, or se plan/operation in text format.

</td>
</tr>
<tr>
<td valign="top">

RETURN\_TYPES

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the list of return types.

</td>
</tr>
<tr>
<td valign="top">

INPUT\_VALUES

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the list of values of input parameters.

</td>
</tr>
<tr>
<td valign="top">

OUTPUT\_VALUES

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the list of values of output parameters.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_ENGINE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the list of all involved execution frameworks.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the default schema of each operator.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of database where procedure is defined.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of schema where procedure is defined.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of outermost procedure.

</td>
</tr>
<tr>
<td valign="top">

SQLSCRIPT\_PLAN\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the SE plan ID.

</td>
</tr>
<tr>
<td valign="top">

SQLSCRIPT\_OPERATOR\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the SE Operation ID.

</td>
</tr>
<tr>
<td valign="top">

SQLSCRIPT\_OPERATOR\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the internal name used in SQLScript.

</td>
</tr>
<tr>
<td valign="top">

NESTED\_STATEMENT\_IDS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the concatenated statement position with respect to SQL inlining.

</td>
</tr>
<tr>
<td valign="top">

SQLSCRIPT\_OPERATOR\_COST

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the estimated cost from the SQLScript optimizer.

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

Displays additional information on the operator.

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

Displays the unique ID of an operator.

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

Displays the operator ID of the parent of an operator.

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

Displays the level from the root operator.

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

Displays the position in the parent operator.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the internal EXPLAIN PLAN command.

</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the target node where the execution is expected to take place in a distributed system.

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

Displays the target node where the execution is expected to take place in a distributed system.

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



<a name="loiod0bbae92c44b489db4b662bb6fed1909__section_ukx_l53_pzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.



<a name="loiod0bbae92c44b489db4b662bb6fed1909__section_h45_vrn_phb"/>

## Additional Information

The OPERATOR\_NAME column can contain **column engine** and **row engine** operators, as shown in the following tables.

Column engine operators:


<table>
<tr>
<th valign="top">

Operator Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

COLUMN SEARCH

</td>
<td valign="top">

Displays the starting position of the column engine operators. OPERATOR\_DETAILS lists the projected columns.

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

Displays information about the accessed column table.

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

Description

</th>
</tr>
<tr>
<td valign="top">

ROW SEARCH

</td>
<td valign="top">

Displays the starting position of row engine operators. OPERATOR\_DETAILS lists projected columns.

</td>
</tr>
<tr>
<td valign="top">

LIMIT

</td>
<td valign="top">

Displays the operator for limiting number of output rows.

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

Displays the operator for joining input relations through B-tree index searches. A join type suffix can be added, for example, a B-tree index join for a left outer join is shown as BTREE INDEX JOIN \(LEFT OUTER\). A join without a join type suffix indicates an inner join.

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

Displays the operator for joining input relations through probing a hash table built on the fly. A join type suffix can be added.

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

Displays the table access through a B-tree index search.

</td>
</tr>
<tr>
<td valign="top">

CPBTREE INDEX SEARCH

</td>
<td valign="top">

Displays the table access through a CPB-tree index search.

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

Displays the operator for aggregating a base table directly.

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

[CALL Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/call-statement-procedural-20d364c.md "Calls a procedure.")

[EXPLAIN PLAN for Call](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/7aabea5031134d2192f7022bc390fce6.html "") :arrow_upper_right:

[CALL](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/729281f732c14860902bcbc5c9cbf6f1.html "") :arrow_upper_right:

[Best Practices for Using SQLScript](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/c59af8fa9ece40f4ba202e12fdacdfdf.html "") :arrow_upper_right:

