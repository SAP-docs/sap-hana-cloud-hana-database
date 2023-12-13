<!-- loio20c4b5cf75191014971a86dc9cad285c -->

# M\_SERVICE\_TRACES System View

Provides configured trace components for each service type.



<a name="loio20c4b5cf75191014971a86dc9cad285c___m__s_e_r_v_i_c_e__t_r_a_c_e_s_1struct_M_SERVICE_TRACES"/>

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

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the service name.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the trace component name.

</td>
</tr>
</table>

**Related Information**  


[M\_SERVICE\_TYPES System View](m-service-types-system-view-20c4d1d.md "Provides information about service types.")

[M\_TRACEFILES System View](m-tracefiles-system-view-20c8f48.md "Provides information about all trace files.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-traces-statement-system-management-20d1281.md "Clears (removes) trace files opened by SAP HANA.")

[ALTER SYSTEM REMOVE TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-traces-statement-system-management-20d25bf.md "Deletes the trace files on a specified host to reduce the disk space used by large trace files.")

[Expensive Statements Trace](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/5faf04f17830464eacdb7938b383d2ab.html "Expensive statements are individual SQL statements whose execution time exceeds a configured threshold. The expensive statements trace records information about these statements for further analysis and is inactive by default.") :arrow_upper_right:

[Traces](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/7e31247372fb4dd7b8c6bbac758b8c91.html "SAP HANA provides various traces for obtaining detailed information about the actions of the database system for troubleshooting and error analysis.") :arrow_upper_right:

[SQL Trace](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/bedc9668bb5710149d56d29fe2632ba0.html "The SQL trace collects information about all SQL statements executed and saves it in a trace file for further analysis. The SQL trace is inactive by default.") :arrow_upper_right:

