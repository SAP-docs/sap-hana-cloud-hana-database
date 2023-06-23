<!-- loio79e35f72f5374ad69dc0811e41339685 -->

# SCHEDULER\_JOBS System View

Shows existing jobs.



<a name="loio79e35f72f5374ad69dc0811e41339685___s_a_m_l__u_s_e_r__m_a_p_p_i_n_g_s_1struct_SAML_USER_MAPPINGS"/>

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

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user who owns the job. The job is executed as this user.



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

PROCEDURE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the called procedure.



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

Displays the name of the called procedure.



</td>
</tr>
<tr>
<td valign="top">

CRON



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schedule of the job.



</td>
</tr>
<tr>
<td valign="top">

START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

If specified, displays the earliest time after which the scheduled job can start to run; otherwise null.



</td>
</tr>
<tr>
<td valign="top">

END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

If specified, displays the latest time before which the scheduled job can start to run; otherwise null.



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

Displays whether the scheduled job can run: TRUE/FALSE.



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

Displays whether the job is valid: TRUE/FALSE. The job may become invalid if the procedure becomes invalid or if the owner of the job no longer has the EXECUTE privilege for the procedure. Invalid job are not scheduled.



</td>
</tr>
<tr>
<td valign="top">

COMMENTS



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays any comment on the job.



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

Displays the time at which the job was created.



</td>
</tr>
</table>



<a name="loio79e35f72f5374ad69dc0811e41339685__section_el4_mkv_b3b"/>

## Additional Information

Users see jobs that they created or on which they have been granted the ALTER or DROP object privilege. Users with the CATALOG READ system privilege see all jobs.

