<!-- loio20d9ec5575191014a251e58ecf90997a -->

# EXPLAIN PLAN Statement \(Data Manipulation\)

Evaluates the execution plan that the database follows when executing an SQL statement.



<a name="loio20d9ec5575191014a251e58ecf90997a__sql_explain_plan_1sql_explain_plan"/>

## Syntax

**Syntax 1:**

```
EXPLAIN RECOMPILED PLAN [ SET STATEMENT_NAME = <statement_name> ] 
   FOR <subquery>
```

**Syntax 2:**

```
EXPLAIN PLAN [ SET STATEMENT_NAME = <statement_name> ] 
   FOR SQL PLAN CACHE ENTRY <plan_id> [ VARIANT <variant_id> ]
```



<a name="loio20d9ec5575191014a251e58ecf90997a__sql_explain_plan_1sql_explain_plan_statement"/>

## Syntax Elements


<dl>
<dt><b>

RECOMPILED

</b></dt>
<dd>

If the target query is a parameterized query, this shows the recompiled plan of the query. Simple queries are not recompiled. Without this keyword, EXPLAIN PLAN shows the plan from the SQL plan cache if it exists, or the precompiled plan of the query if it does not. For other types of queries, this keyword has no effect.

SQL PLAN CACHE ENTRY...VARIANT is not supported with RECOMPILED.



</dd><dt><b>

*<statement\_name\>*

</b></dt>
<dd>

Specifies the name of a specific execution plan in the output table for a given SQL statement.

```
<statement_name> ::= <string_literal>
```



</dd><dt><b>

*<subquery\>*

</b></dt>
<dd>

Specifies the subquery to explain the plan for. For more information about subqueries, see the SELECT statement.



</dd><dt><b>

*<plan\_id\>*

</b></dt>
<dd>

Specifies the identifier of a plan entry to be explained, which is already in the SQL plan cache.

```
<plan_id> ::= <integer_literal>
```



</dd><dt><b>

*<variant\_id\>*

</b></dt>
<dd>

Specifies the identifier of a variant entry to be explained, which is already in the SQL plan cache. SQL PLAN CACHE ENTRY...VARIANT is not supported with RECOMPILED.

```
<variant_id> ::= <integer_literal>
```



</dd>
</dl>



<a name="loio20d9ec5575191014a251e58ecf90997a__section_jkd_llm_wcb"/>

## Permissions

You must have the OPTIMIZER ADMIN system privilege.



<a name="loio20d9ec5575191014a251e58ecf90997a__sql_explain_plan_1sql_explain_plan_description"/>

## Description

Using this command, a user can see the execution plan of a subquery, or that of an entry already in the SQL plan cache. The result of the evaluation is stored in the EXPLAIN\_PLAN\_TABLE view for examination.

The SQL *<subquery\>* must be one of the following type of statements: INSERT, UPDATE, DELETE, REPLACE, UPSERT, MERGE INTO and SELECT. All other type of statements cannot be used with EXPLAIN PLAN. The same rule is applied to the plan cache entry. That is, the cache entry a user specified using *<plan\_id\>* should be a one of the statements listed above.

When plan variant is enabled using a hint or configuration, hex is used by default. This is equivalent to using the use\_hex\_plan hint.



<a name="loio20d9ec5575191014a251e58ecf90997a__sql_explain_plan_1sql_explain_plan_examples"/>

## Example

In the OPERATOR\_NAME of the EXPLAIN\_PLAN\_TABLE system view:

-   COLUMN SEARCH denotes the starting position of column engine operators.

-   ROW SEARCH denotes the starting position of row engine operators.


In the example below, the intermediate result produced by a COLUMN SEARCH \(ID 10\) is consumed by a ROW SEARCH \(ID 7\). The intermediate result produced by the ROW SEARCH \(ID 7\) is consumed by another COLUMN SEARCH \(ID 1\).

The operators below the lowest COLUMN SEARCH \(ID 10\) explain how the COLUMN SEARCH \(ID 10\) is executed.

The operators between the ROW SEARCH \(ID 7\) and the COLUMN SEARCH \(ID 10\) explain how the ROW SEARCH \(ID 7\) processes the intermediate result produced by the COLUMN SEARCH \(ID 10\).

The operators between the top COLUMN SEARCH \(ID 1\) and the ROW SEARCH \(ID 7\) explain how the top COLUMN SEARCH \(ID 1\) processes the intermediate result produced by the ROW SEARCH \(ID 7\).


<table>
<tr>
<th valign="top">

OPERATOR\_NAME

</th>
<th valign="top">

OPERATOR\_ID

</th>
<th valign="top">

PARENT\_OPERATOR\_ID

</th>
<th valign="top">

LEVEL

</th>
<th valign="top">

POSITION

</th>
</tr>
<tr>
<td valign="top">

COLUMN SEARCH

</td>
<td valign="top">

1

</td>
<td valign="top">

NULL

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

LIMIT

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

ORDER BY

</td>
<td valign="top">

3

</td>
<td valign="top">

2

</td>
<td valign="top">

3

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

GROUP BY

</td>
<td valign="top">

4

</td>
<td valign="top">

3

</td>
<td valign="top">

4

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

JOIN

</td>
<td valign="top">

5

</td>
<td valign="top">

4

</td>
<td valign="top">

5

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

COLUMN TABLE

</td>
<td valign="top">

6

</td>
<td valign="top">

5

</td>
<td valign="top">

6

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

ROW SEARCH

</td>
<td valign="top">

7

</td>
<td valign="top">

5

</td>
<td valign="top">

6

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

BTREE INDEX JOIN

</td>
<td valign="top">

8

</td>
<td valign="top">

7

</td>
<td valign="top">

7

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

BTREE INDEX JOIN

</td>
<td valign="top">

9

</td>
<td valign="top">

8

</td>
<td valign="top">

8

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

COLUMN SEARCH

</td>
<td valign="top">

10

</td>
<td valign="top">

9<

</td>
<td valign="top">

\>9

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

FILTER

</td>
<td valign="top">

11

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

COLUMN TABLE

</td>
<td valign="top">

12

</td>
<td valign="top">

11

</td>
<td valign="top">

11

</td>
<td valign="top">

1

</td>
</tr>
</table>

**SQL plan explanation**

Here is an example query plan explanation. In the example, all tables are located on row store.

```
DELETE FROM explain_plan_table WHERE statement_name = 'TPC-H Q10';

EXPLAIN PLAN SET STATEMENT_NAME = 'TPC-H Q10' FOR
   SELECT TOP 20
      c_custkey,
      c_name,
      SUM(l_extendedprice * (1 - l_discount)) AS revenue,
      c_acctbal,
      n_name,
      c_address,
      c_phone,
      c_comment
      FROM
         customer,
         orders,
         lineitem,
         nation
      WHERE
         c_custkey = o_custkey
      AND l_orderkey = o_orderkey
      AND o_orderdate >= '1993-10-01'
      AND o_orderdate < ADD_MONTHS('1993-10-01',3)
      AND l_returnflag = 'R'
      AND c_nationkey = n_nationkey
      GROUP BY
         c_custkey,
         c_name,
         c_acctbal,
         c_phone,
         n_name,
         c_address,
         c_comment
      ORDER BY
         revenue DESC;

   SELECT operator_name, operator_details, table_name
      FROM explain_plan_table
      WHERE statement_name = 'TPC-H Q10';
```

Or, suppose that you execute the following statement, which is the same as the *<subquery\>* in the example above, and then obtain the *<plan\_id\>* = 2050002 of the entry from PLAN\_ID column in M\_SQL\_PLAN\_CACHE monitoring view.

```
SELECT TOP 20
   c_custkey,
   c_name,
   SUM(l_extendedprice * (1 - l_discount)) AS revenue,
   c_acctbal,
   n_name,
   c_address,
   c_phone,
   c_comment
    FROM
       customer,
       orders,
       lineitem,
       nation
    WHERE
       c_custkey = o_custkey
       AND l_orderkey = o_orderkey
       AND o_orderdate >= '1993-10-01'
       AND o_orderdate < ADD_MONTHS('1993-10-01',3)
       AND l_returnflag = 'R'
       AND c_nationkey = n_nationkey
    GROUP BY
       c_custkey,
       c_name,
       c_acctbal,
       c_phone,
       n_name,
       c_address,
       c_comment
    ORDER BY
       revenue DESC;

DELETE FROM explain_plan_table WHERE statement_name = 'TPC-H Q10';

EXPLAIN PLAN SET STATEMENT_NAME = 'TPC-H Q10' FOR SQL PLAN CACHE ENTRY 2050002;

SELECT operator_name, operator_details, table_name
   FROM explain_plan_table
   WHERE statement_name = 'TPC-H Q10';
```

The two examples give the same following result table.


<table>
<tr>
<th valign="top">

OPERATOR\_NAME

</th>
<th valign="top">

OPERATOR\_DETAILS

</th>
<th valign="top">

TABLE\_NAME

</th>
</tr>
<tr>
<td valign="top">

ROW SEARCH

</td>
<td valign="top">

CUSTOMER.C\_CUSTKEY, CUSTOMER.C\_NAME, SUM\(LINEITEM.L\_EXTENDEDPRICE \* \(1 - LINEITEM.L\_DISCOUNT\)\), CUSTOMER.C\_ACCTBAL, NATION.N\_NAME, CUSTOMER.C\_ADDRESS, CUSTOMER.C\_PHONE, CUSTOMER.C\_ COMMENT

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

LIMIT

</td>
<td valign="top">

NUM RECORDS: 20

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

ORDER BY

</td>
<td valign="top">

SUM\(LINEITEM.L\_EXTENDEDPRICE \* \(1 - LINEITEM.L\_DISCOUNT\)\) DESC

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

MERGE AGGREGATION

</td>
<td valign="top">

NUM PARTITIONS: 4

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

GROUP BY

</td>
<td valign="top">

GROUPING: NATION.N\_NAME, R\_CUSTOMER.C\_CUSTKEY, AGGREGATION: SUM\(LINEITEM.L\_EXTENDEDPRICE \* \(1 - LINEITEM.L\_DISCOUNT\)\)

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

CPBTREE INDEX JOIN

</td>
<td valign="top">

INDEX NAME: \_SYS\_TREE\_RS\_279\_\#0\_\#P0,

INDEX CONDITION: ORDERS.O\_ORDERKEY = LINEITEM.L\_ORDERKEY,

INDEX FILTER: 'R' = LINEITEM.L\_RETURNFLAG

</td>
<td valign="top">

LINEITEM

</td>
</tr>
<tr>
<td valign="top">

BTREE INDEX JOIN

</td>
<td valign="top">

INDEX NAME: \_SYS\_TREE\_RS\_285\_\#0\_\#P0,

INDEX CONDITION: CUSTOMER.C\_NATIONKEY = NATION.N\_NATIONKEY

</td>
<td valign="top">

NATION

</td>
</tr>
<tr>
<td valign="top">

BTREE INDEX JOIN

</td>
<td valign="top">

INDEX NAME: \_SYS\_TREE\_RS\_283\_\#0\_\#P0,

INDEX CONDITION: ORDERS.O\_CUSTKEY = CUSTOMER.C\_CUSTKEY

</td>
<td valign="top">

CUSTOMER

</td>
</tr>
<tr>
<td valign="top">

TABLE SCAN

</td>
<td valign="top">

FILTER CONDITION: ORDERS.O\_ORDERDATE < '1994-01-01' AND ORDERS.O\_ORDERDATE \>= '1993-10-01'

</td>
<td valign="top">

ORDERS

</td>
</tr>
</table>

From this plan result we can obtain the following facts about this query:

-   TABLE SCAN is executed on ORDERS with the FILTER CONDITION.

-   BTREE INDEX JOIN is executed with the B-tree index of CUSTOMER and the result of the TABLE SCAN below.

-   BTREE INDEX JOIN is executed with the B-tree index of NATION and the result of the BTREE INDEX JOIN below.

-   CPBTREE INDEX JOIN is executed with the CPB-tree index of LINEITEM and the result of the BTREE INDEX JOIN below.

-   GROUP BY is executed with the result of the CPBTREE INDEX JOIN below, with 4 threads.

-   MERGE AGGREGATION is executed with the result of the GROUP BY below.


**EXPLAIN RECOMPILED PLAN Example**

This example shows the recompiled plan for a parameterized query without executing the query:

```
DROP TABLE tab1;
DROP TABLE tab2;
DELETE FROM sys.explain_plan_table WHERE statement_name = 'explain';
 
CREATE TABLE tab1(a int, b int);
CREATE TABLE tab2(a int, b int);
 
EXPLAIN RECOMPILED PLAN SET STATEMENT_NAME = 'explain' FOR SELECT DISTINCT t1.a FROM tab1 t1 WHERE ? = (SELECT COUNT(DISTINCT t2.b) FROM tab2 t2 WHERE t1.b <= ?) WITH HINT (no_use_hex_plan);
SELECT * FROM sys.explain_plan_table WHERE statement_name = 'explain';
```

