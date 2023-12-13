<!-- loiof55ce8e92a6744f3a4ee9f350cfb6453 -->

# HINTS System View

Provides all available hints to be used in WITH HINT clauses.



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

HINT\_NAME

</td>
<td valign="top">

NVARCHAR\(45\)

</td>
<td valign="top">

Displays the hint name that can be used inside the WITH HINT\(\) syntax.

</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays a description of the hint.

</td>
</tr>
</table>



<a name="loiof55ce8e92a6744f3a4ee9f350cfb6453__section_nq5_prb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[HINT Details](../../010-SQL-Reference/012-SQL-Statements/hint-details-4ba9edc.md "The SQL Optimizer usually determines the access path (for example, index search versus table scan) on the basis of the costs (Cost-Based Optimizer). You can override the SQL Optimizer choice by explicitly specifying hints in the query that enforces a certain access path.")

[STATEMENT\_HINTS System View](statement-hints-system-view-161a91a.md "Provides information about statement hints, including when they were last enabled and/or disabled and by whom.")

[Performance: Using Hints to Query Data Snapshots](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/556a518b49f84d8db770cbd068b94b65.html "Several features in SAP HANA use data snapshots to improve performance. You can use configurable hint classes as a standard way of controlling at run time how the data is selected, either from the snapshot or from the database.") :arrow_upper_right:

[ALTER SYSTEM \{ADD | ALTER | REMOVE\} STATEMENT HINT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-add-alter-remove-statement-hint-statement-system-management-1ec23ef.md "Adds, alters, or removes statement hints from the system to a specified query or statement hash.")

[Managing and Monitoring SAP HANA](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/5c3891048fa44d6983801e0aeaf9af38.html "In addition to the administration tools in the SAP HANA cockpit, other resources are introduced here that are available to you to help improve the performance of your database.") :arrow_upper_right:

[NO_INLINE and INLINE Hints](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/23531168b23340c08731b9660058ee8f.html "The SQLScript compiler combines statements to optimize code. Hints enable you to block or enforce the inlining of table variables.") :arrow_upper_right:

[ROUTE_TO Hint](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/79a9f25f2e9a41e0a4cf03dc6b45a111.html "The ROUTE_TO hint routes the query to the specified volume ID or service type.") :arrow_upper_right:

