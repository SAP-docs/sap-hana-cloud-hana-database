<!-- loioba830ef61250416d8a05e747fecab10b -->

# ABSTRACT\_SQL\_PLANS System View

Lists information about abstract SQL plans.



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

QUERY\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays a number that uniquely identifies the abstract SQL query.



</td>
</tr>
<tr>
<td valign="top">

ABSTRACT\_SQL\_PLAN\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays a number that uniquely identifies each abstract SQL plan entry.



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

Displays the host name of the location where the abstract SQL plan was captured.



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

Displays the port number of the location where the abstract SQL plan was captured.



</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ID of the volume where the abstract SQL plan was captured.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the target statement string.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the MD5 hash value for the STATEMENT\_STRING column.



</td>
</tr>
<tr>
<td valign="top">

PLAN\_KEY



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the key for the abstract SQL plan in JSON format.

These values can affect the generated query execution plans.



</td>
</tr>
<tr>
<td valign="top">

ABSTRACT\_ SQL\_PLAN



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the abstract SQL plan in JSON format. For example:

```
{"alp_rels":[{"alp_Rel":{"alias":"DUMMY",
"alp_id":1,"enumerated_by":139,"field_names":[],
"hash_partition_column":-2147483648,"input_size":1,
"intermediate_alternative":false,"is_ap_injected":false,"is_esx_node":false,
"is_view_cache":false,"join_table_name":"NULL","locationName":"selibm57:36903",
"locked":false,"logically_enumerated":false,"multi_container_id":-1,
"output_column_size":1,"partition_search_ids":[],"physical_operator_type":22,
"referenced_cols":[{"col":0}],"rel_id":1000000,"rel_type":6,"schema_name":"SYS",
"table_name":"DUMMY","table_type":0,"trex_externalkey_pos":-2147483648,
"trex_rel_id":-1,"trex_rowid_needed":false,"trex_rowid_pos":-2147483648,
"used_cols":[{"col":0}]}},{"alp_Rel":{"alp_id":0,"child_rel_id":1,
"enumerated_by":139,"intermediate_alternative":false,"is_esx_node":false,
"locationName":"selibm57:36903","locked":false,"logically_enumerated":true,
"output_column_size":0,"physical_operator_type":0,
"project_col_aliases":[{"alias":"NULL"}],"project_col_labels":[{"label":"DUMMY"}],
"project_cols":[{"alp_Exp":{"col_id":0,"exp_type":0,"field_name":"DUMMY",
"is_grouping_id":false,"is_table_key":false,"org_table_name":"DUMMY",
"position":-1,"prefetch":false,"promoted_type":{"ftc":0,"length":-1,"scale":0},
"real_result_type":{"ftc":8,"length":1,"scale":0},"rel_id":1000000,
"result_type":{"ftc":29,"length":1,"scale":0},"schema_name":"SYS",
"table_name":"DUMMY"}}],"rel_type":3,"trex_rel_id":-1}}],
"applied_migrator_set":["3.0","4.0","5.0"],"related_objects":[{"object_id":132355,
"object_name":"SYS.DUMMY","object_type":1,"object_version":1},
{"object_id":135526,"object_name":"DUMMY","object_type":7,
"object_version":1}],"root_rel_id":0}
```



</td>
</tr>
<tr>
<td valign="top">

RELATED\_OBJECTS



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays related object information for the captured abstract SQL plan.



</td>
</tr>
<tr>
<td valign="top">

ABSTRACT\_SQL\_PLAN\_VERSION



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the abstract SQL plan version with applied migration information.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the abstract SQL plan will be used \(TRUE\) or not \(FALSE\).



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

Displays whether the abstract SQL plan is valid \(TRUE\) or invalid \(FALSE\).



</td>
</tr>
<tr>
<td valign="top">

DETAILS



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays additional information on the abstract SQL plan, including invalidation reasons.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ENABLE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp when the abstract SQL plan was added or last enabled.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ENABLE\_USER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the ID of the user who added or last enabled the abstract SQL plan.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp when the abstract SQL plan was last disabled.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_USER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the ID of the user who last disabled the abstract SQL plan.



</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp when the abstract SQL plan was captured.



</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_USER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the ID of the user who captured the abstract SQL plan.



</td>
</tr>
</table>

**Related Information**  


[M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View](../022-Monitoring-Views/m-abstract-sql-plan-overview-system-view-03aa3ad.md "Provides the status of each Plan Stability Manager on every index server in SAP HANA.")

[M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](../022-Monitoring-Views/m-abstract-sql-plan-statistics-system-view-35af7f2.md "Provides SQL query runtime statistics.")

