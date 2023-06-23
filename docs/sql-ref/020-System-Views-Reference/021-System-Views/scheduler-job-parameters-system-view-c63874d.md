<!-- loioc63874da0e89479aa7919291abcbc144 -->

# SCHEDULER\_JOB\_PARAMETERS System View

Shows parameters for the jobs.




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

SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the job.



</td>
</tr>
<tr>
<td valign="top">

SCHEDULER\_JOB\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the job.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the parameter.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_VALUE



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the parameter value as a Unicode string.



</td>
</tr>
</table>



<a name="loioc63874da0e89479aa7919291abcbc144__section_el4_mkv_b3b"/>

## Additional Information

Users see jobs that they created or on which they have been granted the ALTER or DROP object privilege. Users with the CATALOG READ system privilege see parameters for all jobs.

