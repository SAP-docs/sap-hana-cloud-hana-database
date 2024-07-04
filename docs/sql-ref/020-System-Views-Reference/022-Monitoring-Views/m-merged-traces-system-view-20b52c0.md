<!-- loio20b52c0075191014a43fb02951633999 -->

# M\_MERGED\_TRACES System View

Contains the merged content of the server trace files for all of the SAP HANA services.



<a name="loio20b52c0075191014a43fb02951633999___m__m_e_r_g_e_d__t_r_a_c_e_s_1struct_M_MERGED_TRACES"/>

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

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database user.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user.

</td>
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

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction ID.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the update transaction ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statement ID.

</td>
</tr>
<tr>
<td valign="top">

THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of thread that wrote trace entry.

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

Displays the time when trace entry was written.

</td>
</tr>
<tr>
<td valign="top">

TRACE\_LEVEL

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the trace level.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the trace component.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the source file which contains the trace.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_FILE\_LINE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the source file line.

</td>
</tr>
<tr>
<td valign="top">

TRACE\_TEXT

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the traced text.

</td>
</tr>
<tr>
<td valign="top">

TRACE\_FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the trace file containing the trace entry.

</td>
</tr>
<tr>
<td valign="top">

TRACE\_FILE\_LINE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the trace file line.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application name.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application source.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ROOTCONTEXT\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID identifying the source of request.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRANSACTION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID identifying the business transaction.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID identifying the connection.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_COUNTER

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the extended passport \(EPP\) connection counter.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) component name of the initial/root context.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_COMPONENT\_TYPE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) component type.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ACTION

</td>
<td valign="top">

NVARCHAR\(40\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) component action.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ACTION\_TYPE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) component action type.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_PREVIOUS\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) passport component name of the previous context.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_SERVICE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) service.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_USER\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) user ID.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CLIENT

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) client.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRACE\_FLAGS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) trace flags.

</td>
</tr>
<tr>
<td valign="top">

W3C\_TRACE\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the W3C trace context ID, which is identical to the PASSPORT\_TRANSACTION\_ID.

</td>
</tr>
<tr>
<td valign="top">

W3C\_SPAN\_ID

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the W3C trace context span ID, which is derived from the PASSPORT\_CONNECTION\_ID and PASSPORT\_CONNECTION\_COUNTER.

</td>
</tr>
</table>

**Related Information**  


[MERGE INTO Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/merge-into-statement-data-manipulation-3226201.md "Merges data into an existing column store table.")

[The Delta Merge Operation](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bd9ac728bb57101482b2ebfe243dcd7a.html "Write operations are only performed on the delta storage. The delta merge operation optimizes the data and transfers it to the main storage.") :arrow_upper_right:

[Traces](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/7e31247372fb4dd7b8c6bbac758b8c91.html "") :arrow_upper_right:

