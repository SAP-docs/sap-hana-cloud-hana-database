<!-- loio5e83abee7b454624b1530f363bbd67a6 -->

# M\_ALL\_JOBS

View information about the progress of the individual jobs linked with container operations.



The `M_ALL_JOBS` view enables you to display information about the progress of the individual jobs that concern selected container operations.



**M\_ALL\_JOBS**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

REQUEST\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

The unique ID of the API call that produced this job. This ID is always the same for jobs that originate from the same API call.



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

The user who called the \(`ASYNC_`\)



</td>
</tr>
<tr>
<td valign="top">

APPUSER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The application user who called the `(ASYNC_)MAKE API` 



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

The identifier of the connection that started the `(ASYNC_)MAKE` 



</td>
</tr>
<tr>
<td valign="top">

START\_TIMESTAMP\_UTC



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The UTC time when the `(ASYNC_)MAKE` was started



</td>
</tr>
<tr>
<td valign="top">

JOB\_START\_TIMESTAMP\_UTC



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The UTC time when the current job started



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_JOB



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

The numeric identifier of the currently running job



</td>
</tr>
<tr>
<td valign="top">

NUM\_JOBS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

The total number of jobs that will run



</td>
</tr>
<tr>
<td valign="top">

STATUS



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The current status of the job, for example: Finished, Committed, Simulated, Rolled back, Post commit steps



</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TIMESTAMP\_UTC



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

UTC time when the job information was last updated



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_CONNECTION\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The identifier of the internal connection used by HDI



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_CONNECTION\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The time when the internal connection started



</td>
</tr>
<tr>
<td valign="top">

IS\_INTERNAL\_CONNECTION\_ACTIVE



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

TRUE \(or FALSE\): indicates that the job is still running \(or not\)



</td>
</tr>
<tr>
<td valign="top">

GROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the container group associated with the running job



</td>
</tr>
</table>

