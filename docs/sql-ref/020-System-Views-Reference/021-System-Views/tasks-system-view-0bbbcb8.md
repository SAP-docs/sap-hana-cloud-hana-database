<!-- loio0bbbcb8a7ed54b7fb0efb875dd7e26f1 -->

# TASKS System View

Provides information regarding table tasks.



<a name="loio0bbbcb8a7ed54b7fb0efb875dd7e26f1__section_ayk_2mk_vhb"/>

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

TASK\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the unique identifier for the task.



</td>
</tr>
<tr>
<td valign="top">

TASK\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the task.



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

Displays the schema that the task was created in.



</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the owner of the task.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the creation time.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory size of loaded task in bytes.



</td>
</tr>
<tr>
<td valign="top">

TASK\_TYPE



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the type of task derived from the task plan.



</td>
</tr>
<tr>
<td valign="top">

PLAN\_VERSION



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the version of the task plan.



</td>
</tr>
<tr>
<td valign="top">

PLAN



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the task plan used to define the task. This value is NULL if the task was created using a procedure.



</td>
</tr>
<tr>
<td valign="top">

COMMENTS



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the description of the task from the task plan.



</td>
</tr>
<tr>
<td valign="top">

HAS\_TABLE\_TYPE\_INPUT



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the task is modeled with a table type as input: TRUE/FALSE. If TRUE, this means that data would need to be pushed at execution time.



</td>
</tr>
<tr>
<td valign="top">

HAS\_SDQ



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the task contains SDQ \(Smart Data Quality\) functionality: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_REALTIME\_TASK



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the specified task is a realtime task.



</td>
</tr>
<tr>
<td valign="top">

IS\_VALID



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the task is in a valid state: TRUE/FALSE. FALSE indicates that the task has been invalidated by a dependency.



</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_ONLY



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the task is read only, meaning it has only table type outputs: TRUE/FALSE. FALSE indicates that the task writes to non-table-type outputs.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_SCHEMA



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

If the task was created with a procedure instead of a plan, contains the schema name of the stored procedure.



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

If the task was created with a procedure instead of a plan, contains the name of the stored procedure.



</td>
</tr>
<tr>
<td valign="top">

INPUT\_PARAMETER\_COUNT



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the number of input \(tableType\) parameters.



</td>
</tr>
<tr>
<td valign="top">

OUTPUT\_PARAMETER\_COUNT



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the number of output \(tableType\) parameters.



</td>
</tr>
<tr>
<td valign="top">

SQL\_SECURITY



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the security model for the task: DEFINER/INVOKER.



</td>
</tr>
</table>

**Related Information**  


[TASK\_PARAMETERS System View](task-parameters-system-view-0853c4b.md "Provides task parameter information.")

[M\_TASKS System View](../022-Monitoring-Views/m-tasks-system-view-5c8f947.md "Provides task monitoring information.")

