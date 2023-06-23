<!-- loio5a5f9f0efe9544769977e5ef45defc1f -->

# DROP SCHEDULER JOB Statement \(Data Definition\)

Drops a scheduled job in the current or specified schema.



<a name="loio5a5f9f0efe9544769977e5ef45defc1f__sql_create_remote_source_1sql_create_remote_source_syntax"/>

## Syntax

```
DROP SCHEDULER JOB [ <schema_name>.] <job_name> 
```



<a name="loio5a5f9f0efe9544769977e5ef45defc1f__sql_create_remote_source_1sql_create_remote_source"/>

## Syntax Elements


<dl>
<dt><b>

*<job\_name\>*

</b></dt>
<dd>

Specifies the name of the scheduled job being dropped.



</dd>
</dl>



<a name="loio5a5f9f0efe9544769977e5ef45defc1f__section_opr_ddt_5cb"/>

## Permissions

This statement requires that you own the scheduled job or have the DROP object privilege on the scheduled job.



<a name="loio5a5f9f0efe9544769977e5ef45defc1f__sql_create_remote_source_1sql_create_remote_source_examples"/>

## Example

This example drops the scheduler job schedule1

```
DROP SCHEDULER JOB schedule1;
```

