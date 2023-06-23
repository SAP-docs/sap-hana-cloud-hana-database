<!-- loioafa22f3bfcab4d5e8bac20529209ae56 -->

# M\_SQL\_PLAN\_ADVISOR System View

Provides information on the running status of SQL Plan Advisor.




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

REGISTRATION\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the unique ID of a target registration on SQL plan advice.



</td>
</tr>
<tr>
<td valign="top">

ADVICE\_TYPE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the type of the SQL plan tuning advice. NULL appears for the record representing the original plan.



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

Displays the user name of the target query.



</td>
</tr>
<tr>
<td valign="top">

SESSION\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the session user name of the target query.



</td>
</tr>
<tr>
<td valign="top">

REGISTRATION\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user name of the registered target.



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

Displays the schema name of target query.



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

Displays the statement hash of target query.



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

Displays the statement string of target query.



</td>
</tr>
<tr>
<td valign="top">

SHARING\_SCHEMA\_USER\_SET



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the schema or user pool in which the plan can be shared if the target is a inter-user sharing plan; NULL otherwise.



</td>
</tr>
<tr>
<td valign="top">

STATUS



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the status of alternative plan evaluation and application.



</td>
</tr>
<tr>
<td valign="top">

APPLY\_TYPE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the requested apply type. Valid values: AUTOMATIC or MANUAL.



</td>
</tr>
<tr>
<td valign="top">

APPLY\_REASON



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the reason why the advice was applied.



</td>
</tr>
<tr>
<td valign="top">

CONFIDENCE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the confidence of the advice.



</td>
</tr>
<tr>
<td valign="top">

REGISTRATION\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of the registration.



</td>
</tr>
<tr>
<td valign="top">

APPLY\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of the advice application.



</td>
</tr>
<tr>
<td valign="top">

AVG\_COMPLIE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average compile time in microseconds.



</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average execution time in microseconds.



</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CPU\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average execution CPU time in microseconds.



</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average execution memory size in bytes.



</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the execution count.



</td>
</tr>
<tr>
<td valign="top">

MINIMUM\_EXECUTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum test count.



</td>
</tr>
<tr>
<td valign="top">

DETAIL



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays details of the plan.



</td>
</tr>
<tr>
<td valign="top">

HOST



</td>
<td valign="top">

NVARCHAR



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

VOLUMN\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the persistence volume ID.



</td>
</tr>
</table>

