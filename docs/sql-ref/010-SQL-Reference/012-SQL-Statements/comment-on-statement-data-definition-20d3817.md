<!-- loio20d3817075191014ba7bcfdbab508d0e -->

# COMMENT ON Statement \(Data Definition\)

Adds a comment to an object in the database, or removes an existing comment.



## Syntax

```
COMMENT ON <object_type> <object_name> IS <comment>
```



<a name="loio20d3817075191014ba7bcfdbab508d0e__sql_comment_on_1sql_comment_on_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<object\_type\>*

</b></dt>
<dd>

Specifies the type of object to add the comment on.

```
<object_type> ::=
 TABLE
 | VIEW
 | COLUMN
 | USER
 | ROLE
 | USERGROUP
 | SCHEDULER JOB
 | ROLEGROUP
 | CERTIFICATE
 | PUBLIC KEY 
```



</dd><dt><b>

*<object\_name\>*

</b></dt>
<dd>

Specifies the name of the object to add a commented on, with optional schema name.

```
<object_name> ::= [<schema_name>.]<identifier>
```



</dd><dt><b>

*<comment\>*

</b></dt>
<dd>

Specifies the comment for the object.

```
<comment> ::= <string_literal> | NULL
```

If NULL is specified, then any existing comment is dropped.



</dd>
</dl>



<a name="loio20d3817075191014ba7bcfdbab508d0e__sql_comment_on_1sql_comment_on_description"/>

## Description

Comments are a useful way to record an intuitive description of objects in the database such as tables, columns, and users. You can also remove comments.



<a name="loio20d3817075191014ba7bcfdbab508d0e__section_stf_q2d_pbb"/>

## Permissions

To add or remove comments on an object, you must have the following object-specific privileges:

-   For tables, views, and view columns: ALTER object privilege on the table or view
-   For users: OPERATOR object privilege on the user group of the user
-   For roles: ROLE ADMIN if the role is not in a role group, otherwise either the GRANTOR or OPERATOR object privilege on the role group that role is assigned
-   For user groups: OPERATOR object privilege on the user group
-   For scheduler jobs: ALTER object privilege on the scheduler job
-   For role groups: GRANTOR or OPERATOR object privilege on the role group
-   For certificates and public keys: CERTIFICATE ADMIN system privilege



<a name="loio20d3817075191014ba7bcfdbab508d0e__sql_comment_on_1sql_comment_on_examples"/>

## Examples


<dl>
<dt><b>

Comment on a table

</b></dt>
<dd>

Create a table and add a comment on it.

```
CREATE ROW TABLE COMMENT_ON_EX(A INT);
 COMMENT ON TABLE COMMENT_ON_EX IS 'Used for comment on examples';
```

Select the table from the TABLES system table to view the comment.

```
SELECT * FROM TABLES WHERE table_name='COMMENT_ON_EX';
```



</dd><dt><b>

Comment on a table column

</b></dt>
<dd>

Comment on column A of the COMMENT\_ON\_EX table from example 1.

```
COMMENT ON COLUMN COMMENT_ON_EX.A IS 'This is an example column comment';
```

Select the column description from the TABLE\_COLUMNS system table.

```
SELECT * FROM TABLE_COLUMNS WHERE table_name='COMMENT_ON_EX'; 
```



</dd><dt><b>

Comment on a view and view column

</b></dt>
<dd>

Create a view, a view comment, and view column comment.

```
CREATE VIEW COMMENT_ON_EX_VIEW AS SELECT * FROM COMMENT_ON_EX;
 COMMENT ON VIEW COMMENT_ON_EX_VIEW IS 'This is a view comment';
 COMMENT ON COLUMN COMMENT_ON_EX_VIEW.A IS 'This is a view column comment';
```

Select the view comment and view column comments from the relevant system tables.

```
SELECT * FROM VIEWS WHERE view_name='COMMENT_ON_EX_VIEW';
 SELECT * FROM VIEW_COLUMNS WHERE view_name='COMMENT_ON_EX_VIEW';
```



</dd><dt><b>

Comment on a scheduler job

</b></dt>
<dd>

Create a scheduled job and a scheduler job comment.

```
CREATE SCHEDULER JOB retention_job CRON '* * * * 1 30 01' ENABLE PROCEDURE RETENTION_JOB PARAMETERS DAYS=14
COMMENT ON SCHEDULER JOB retention_job IS ‘This job implements a retention policy’;
```



</dd><dt><b>

Remove comments

</b></dt>
<dd>

Drop a view comment and a view column comment.

```
COMMENT ON VIEW COMMENT_ON_EX_VIEW IS NULL;
COMMENT ON COLUMN COMMENT_ON_EX_VIEW.A IS NULL;
```



</dd>
</dl>

**Related Information**  


[TABLES System View](../../020-System-Views-Reference/021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/table-columns-system-view-2100d33.md "Provides information about available table columns.")

[VIEWS System View](../../020-System-Views-Reference/021-System-Views/views-system-view-2102bf2.md "Lists available views.")

[VIEW\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/view-columns-system-view-21028f1.md "Lists available view columns.")

