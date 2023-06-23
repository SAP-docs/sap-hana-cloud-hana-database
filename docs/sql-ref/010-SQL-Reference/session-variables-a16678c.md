<!-- loioa16678c085bf475f832c10b2629f3997 -->

# Session Variables

 



The following table lists predefined session variables and whether they can be set by the user \(using a SET statement\) or a client \(API\) call, or whether they are set exclusively by the server.


<table>
<tr>
<th valign="top">

Predefined Variable \(M\_SESSION\_CONTEXT.KEY\)



</th>
<th valign="top">

Value Constraint



</th>
<th valign="top">

Set by



</th>
<th valign="top">

In M\_SESSION\_CONTEXT



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

APPLICATION



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the application name.

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONVERSION



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the application version information. Applications can use their "own" version naming, no format is predefined

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONUSER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the application-defined user name.

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONACTION



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies that with APPLICATIONACTION the application can define which logical action/step it is currently performing.

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONCOMPONENT



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the name of the application component.

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONCOMPONENTTYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the type of application component. For example, UPD.

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONSOURCE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies that with APPLICATIONSOURCE the application can define from which source file SAP HANA was called.

The usage is up to the application and could be something like one of the following examples:

-   *<abap\_program\_name\>*:*<line\_number\>*
-   *<java\_source\_file\_name\>*:*<line\_number\>*
-   *<package\_name\>*/*<file\_name\>*:*<line\_number\>*

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

APPLICATIONTENANT



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies a mapping of a connection to a workload class. Configure this session variable with a corresponding APPLICATION TENANT NAME workload mapping property to complete the mapping \(for example, `SET 'APPLICATIONTENANT'='TENANT1';`\).

**Server usage**: Traces, statistical data and trace filters



</td>
</tr>
<tr>
<td valign="top">

CASE\_SENSITIVE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Only if set to FALSE



</td>
<td valign="top">

Specifies that with CASE\_SENSITIVE set to TRUE, only the exact match is found. With CASE\_SENSITIVE set to FALSE, any upper/lowercase combination of the search string is found. The default is TRUE.

If a case-insensitive search or compare is done outside of a filter on a table, the corresponding columns may be returned in uppercase. This is because an UPPER function is applied by the optimizer to influence the result to achieve a case-insensitive search. For example, `SELECT * FROM TAB WHERE a LIKE '%a%'` works well, but `SELECT * FROM tab1 WHERE name LIKE '%case%' UNION SELECT * FROM tab2 WHERE name LIKE '%case%'` returns the results in uppercase due the required union comparison.

Also, CASE\_SENSITIVE is only supported for NVARCHAR values and only for these operations:

-   WHERE \(including LIKE\)
-   JOIN
-   HAVING
-   CASE
-   GROUP BY
-   ORDER BY
-   Window functions
-   UNION

**Server usage**: Defines the case-sensitivity during the search.



</td>
</tr>
<tr>
<td valign="top">

DATE\_FORMAT



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the default DAYDATE format to apply for the session.

**Server usage**: No



</td>
</tr>
<tr>
<td valign="top">

DEBUG\_TOKEN



</td>
<td valign="top">

VARCHAR\(32\)



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies that with DEBUG\_TOKEN you can set a session variable, used by the debugger, to attach criterion.

If you specify that the debugger is to only attach to connections where a certain debug token is set, it attaches only to the ones where the DEBUG\_TOKEN session variable is set and ignores others.

**Server usage**: M\_DEBUG\_SESSIONS.ATTACH\_FILTER\_DEBUG\_TOKEN



</td>
</tr>
<tr>
<td valign="top">

ENABLE\_ABSTRACT\_SQL\_PLAN\_ENTRY



</td>
<td valign="top">

 



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the ID of the SQL plan that is enabled in the current session.

When the query for this plan is executed, a comment is appended to the statement so that it can be identified in the plan cache.



</td>
</tr>
<tr>
<td valign="top">

PROTOCOL\_VERSION



</td>
<td valign="top">

\-



</td>
<td valign="top">

Server



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the protocol version of the client interface libraries, formatted as: *<protocol\_version\>* \(*<distribution\_protocol\_version\>*, *<data\_format\_version\>*\). For example, 4.1 \(1,1\)

**Server usage**: Internal



</td>
</tr>
<tr>
<td valign="top">

SECONDDATE\_FORMAT



</td>
<td valign="top">



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the default SECONDDATE format to apply for the session.

**Server usage**: No



</td>
</tr>
<tr>
<td valign="top">

SPATIAL\_OUTPUT\_REPRESENTATION



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the output format of ST\_Geometry and ST\_Point. Valid options are WKB, the default, and EWKB.



</td>
</tr>
<tr>
<td valign="top">

TEMPORAL\_SYSTEM\_TIME\_AS\_OF



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

For use with system-versioned tables. Setting this session variable automatically adds a FOR SYSTEM\_TIME AS OF clause to all system-versioned tables contained in subsequent SELECT statements \(assuming a FOR SYSTEM\_TIME AS OF is not already specified in the SELECT statement\).

**Server usage**: No



</td>
</tr>
<tr>
<td valign="top">

TEMPORAL\_APPLICATION\_TIME\_AS\_OF



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

For use with application-time period tables. Setting this session variable automatically adds a FOR APPLICATION\_TIME AS OF clause to all application-time period tables contained in subsequent SELECT statements \(assuming a FOR APPLICATION\_TIME AS OF is not already specified in the SELECT statement\).

**Server usage**: No



</td>
</tr>
<tr>
<td valign="top">

TIME\_FORMAT



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the default TIME format to apply for the session.

**Server usage**: No



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP\_FORMAT



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the default TIMESTAMP format to apply for the session.

**Server usage**: No



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_ROWCOUNT



</td>
<td valign="top">

Integer



</td>
<td valign="top">

Server



</td>
<td valign="top">

No, only accessible from: `SELECT session_context('TOTAL_ROWCOUNT') FROM DUMMY`.



</td>
<td valign="top">

Specifies the total row count. Specifying SELECT ... LIMIT x returns up to x rows. With the optional TOTAL ROWCOUNT the \(estimated\) total number of rows is set in TOTAL\_ROWCOUNT variable. This variable is not deleted/reset by non TOTAL ROWCOUNT statements. The similar SELECT TOP x ... does not support this extension.

This feature is only supported for column tables and column views. It can return exact or estimated row count or only the given LIMIT. The concrete return value depends on the statement, used tables and views and internally chosen SQL optimizer strategy. Usage is recommended only for interactive paged searches to show information like "result 11 to 20 of estimated 50000".

**Server usage**: SELECT ... LIMIT x TOTAL ROWCOUNT



</td>
</tr>
<tr>
<td valign="top">

TRACEPROFILE



</td>
<td valign="top">

\-



</td>
<td valign="top">

User/Client



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the name of the trace profile. This is used for manual activation of trace profiles defined in inifiles as \[traceprofile\_*<name\>*\]

The value can contain one traceprofile name or a comma separated list of traceprofile names.

**Server usage**: Trace filter



</td>
</tr>
</table>

**Related Information**  


[M\_SESSION\_CONTEXT System View](../020-System-Views-Reference/022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

[SET \[SESSION\] Statement \(Session Management\)](012-SQL-Statements/set-session-statement-session-management-20fd82b.md "Sets a session variable for the current session.")

[UNSET \[SESSION\] Statement \(Session Management\)](012-SQL-Statements/unset-session-statement-session-management-20fec78.md "Unsets a session variable for the current session.")

[CREATE WORKLOAD MAPPING Statement \(Workload Management\)](012-SQL-Statements/create-workload-mapping-statement-workload-management-996978a.md "Defines workload mappings.")

[WORKLOAD\_MAPPINGS System View](../020-System-Views-Reference/021-System-Views/workload-mappings-system-view-89a0660.md "Provides information about available workload mappings.")

