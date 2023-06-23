<!-- loiod7d43d818366460dae1328aab5d5df4f -->

# CREATE SCHEDULER JOB Statement \(Data Definition\)

Creates a scheduled job in the current or specified schema.



<a name="loiod7d43d818366460dae1328aab5d5df4f__sql_create_remote_source_1sql_create_remote_source_syntax"/>

## Syntax

```
CREATE SCHEDULER JOB [ <schema_name>.] 
<job_name> 
   CRON '<cron>' [ <job_recurrence_range> ]
   [ ENABLE | DISABLE ] PROCEDURE [ <schema_name>.]<procedure_name>
   [ PARAMETERS <parameter_list> ]<NAME>=<CONST_EXPR> [, <NAME>=<CONST_EXPR>[, ...] ] ]
```



<a name="loiod7d43d818366460dae1328aab5d5df4f__sql_create_remote_source_1sql_create_remote_source"/>

## Syntax Elements


<dl>
<dt><b>

*<job\_name\>*

</b></dt>
<dd>

Specifies the name of the scheduled job.



</dd><dt><b>

*<cron\>*

</b></dt>
<dd>

Specifies the frequency of the job.

```
<cron> ::= <year> <month> <date> <weekday> <hour> <minute> <seconds> 
```


<dl>
<dt><b>

*<year\>*

</b></dt>
<dd>

A four-digit number.



</dd><dt><b>

*<month\>*

</b></dt>
<dd>

A number from 1 to 12.



</dd><dt><b>

*<date\>*

</b></dt>
<dd>

A number from 1 to 31.



</dd><dt><b>

*<weekday\>*

</b></dt>
<dd>

A three-character day of the week: mon,tue,wed,thu,fri,sat,sun.



</dd><dt><b>

*<hour\>*

</b></dt>
<dd>

A number from 0 to 23 \(expressed in 24-hour format\).



</dd><dt><b>

*<minute\>*

</b></dt>
<dd>

A number from 0 to 59.



</dd><dt><b>

*<seconds\>*

</b></dt>
<dd>

A number from 0 to 59.



</dd>
</dl>

Each cron field also supports wildcard characters as follows.


<table>
<tr>
<th valign="top">

Character



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

\*



</td>
<td valign="top">

Any value.



</td>
</tr>
<tr>
<td valign="top">

\*/n



</td>
<td valign="top">

Any n-th value. For example, \*/1 for the day of the month means run every day of the month, \*/3 means run every third day of the month.



</td>
</tr>
<tr>
<td valign="top">

a:b



</td>
<td valign="top">

Any value between a and b.



</td>
</tr>
<tr>
<td valign="top">

a:b/n



</td>
<td valign="top">

Any n-th value between a and b. For example, 1:10/3 for the day of the month means every 3rd day between 1 and 10 or the 3rd, 6th, and 9th day of the month.



</td>
</tr>
<tr>
<td valign="top">

n.a



</td>
<td valign="top">

\(For *<weekday\>* only\) A day of the week where n is a number from -5 to 5 for the n-th occurrence of the day in week a. For example, for the year 2019, 2.3 means Tuesday, January 15th. -3.22 means Friday, May 31st..



</td>
</tr>
</table>



</dd><dt><b>

*<job\_recurrence\_range\>*

</b></dt>
<dd>

Specifies the range for the recurrence of the scheduled job. If this value is not specified, then the recurrence of the scheduled job never ends.

```
<job_recurrence_range> ::= FROM <start_time> ] [ UNTIL <end_time>
```


<dl>
<dt><b>

*<start\_time\>*

</b></dt>
<dd>

Specifies the earliest time after which the scheduled job can start to run.



</dd><dt><b>

*<end\_time\>*

</b></dt>
<dd>

Specifies the latest time before which the scheduled job can start to run.



</dd>
</dl>



</dd><dt><b>

ENABLE | DISABLE

</b></dt>
<dd>

Specifies whether the scheduled job will run once the next scheduled time is reached. Use ALTER SCHEDULER JOB to enable a disabled scheduled job. If this clause is not specified, then the job is disabled by default.



</dd><dt><b>

*<parameter\_list\>*

</b></dt>
<dd>

Specifies the parameter for the specified procedure, in a comma-separated list of *<name\>* = *<constant\_expression\>*.

```
<parameter_list> ::= <parm_name>=<parm_expression> [, <parm_name>=<parm_expression> [,...] ]

<parm_expression> ::= <name> = <constant_expression>
```

All IN or INOUT parameters without a DEFAULT must be provided.



</dd>
</dl>



<a name="loiod7d43d818366460dae1328aab5d5df4f__section_opr_ddt_5cb"/>

## Permissions

This statement requires the CREATE ANY privilege in the schema where the scheduled job was created and the EXECUTE privilege on the procedure referenced by the scheduled job.



<a name="loiod7d43d818366460dae1328aab5d5df4f__sql_create_remote_source_1sql_create_remote_source_examples"/>

## Example

This example creates the retention\_job scheduler job that runs from Monday to Friday at 1:23:45 and calls the procedure RETENTION\_PROCEDURE. The three \* mean that the scheduled job can run on any date \( year month day\). The job is enabled and the RETENTION\_PROCEDURE requires the DAYS parameter, which is set to 14 in this example.

 

```
CREATE SCHEDULER JOB RETENTION_JOB CRON ‘* * * mon,tue,wed,thu,fri 1 23 45’ 
    ENABLE PROCEDURE RETENTION_PROCEDURE PARAMETERS DAYS=14;
```

**Related Information**  


[ALTER SCHEDULER JOB Statement \(Data Definition\)](alter-scheduler-job-statement-data-definition-701e467.md "Alters a scheduled job in the current or specified schema.")

