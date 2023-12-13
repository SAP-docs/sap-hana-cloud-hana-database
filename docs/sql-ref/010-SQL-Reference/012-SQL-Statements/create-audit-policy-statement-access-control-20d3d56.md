<!-- loio20d3d56075191014af43d6487fcaa603 -->

# CREATE AUDIT POLICY Statement \(Access Control\)

Creates an audit policy.



<a name="loio20d3d56075191014af43d6487fcaa603__sql_create_audit_policy_1sql_create_audit_policy_syntax"/>

## Syntax

```
CREATE AUDIT POLICY <policy_name> AUDITING <audit_status> <audit_actions>
   LEVEL <audit_level> [ <opt_audit_trail_type> ]
```



<a name="loio20d3d56075191014af43d6487fcaa603__sql_create_audit_policy_1sql_create_audit_policy_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<policy\_name\>*

</b></dt>
<dd>

Specifies the name of the audit policy to be created.

```
<policy_name> ::= <identifier>
```



</dd><dt><b>

*<audit\_status\>*

</b></dt>
<dd>

Defines whether successful, unsuccessful, or all executions of the specified audit actions are audited.

```
<audit_status> ::= 
   { SUCCESSFUL 
   | UNSUCCESSFUL 
   | ALL }
```



</dd><dt><b>

*<audit\_actions\>*

</b></dt>
<dd>

Specifies the audit actions for the audit policy.

```
<audit_actions> ::= 
   { <actions_for_principals>
   | <audit_action_list>
   | <target_audit_action_list>
   | <schema_audit_action_list> }
```


<dl>
<dt><b>

*<actions\_for\_principals\>*

</b></dt>
<dd>

Specifies that commands executed by a user or a set of users or all users except the named set of users are audited.

```
<actions_for_user> ::= ACTIONS [ EXCEPT ] FOR <user_name> [, <user_name> [,...] ]
```


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the username of the user to be audited by the audit policy.

```
<user_name> ::= <identifier>
```



</dd>
</dl>



</dd><dt><b>

*<audit\_action\_list\>*

</b></dt>
<dd>

Audits specific system actions, optionally limited by *<principal\_list\>*.

```
<audit_action_list> ::= 
   <audit_action_name> [, <audit_action_name> [,...] ]
   [ [ EXCEPT ] FOR <principal_list>
```

For the complete list of possible values for *<audit\_action\_name\>*, see the table of audit actions provided in the **Description** section of this topic.


<dl>
<dt><b>

*<principal\_list\>*

</b></dt>
<dd>

Specifies the principals whose actions or whose members’ actions are to be audited or excluded from auditing. Principals can be users, usergroups, or a set of users and usergroups.

```
<principal_list> ::= 
   { <user_name> [, <user_name> [,...] ]
   | PRINCIPALS [ { USER <user_name> | USERGROUP <usergroup_name> } ] [,...] ] }
```



</dd>
</dl>



</dd><dt><b>

*<target\_audit\_action\_list\>*

</b></dt>
<dd>

Audits actions on a database object or a set of objects. Optionally, this auditing can be limited to a user or a set of users or audited for all users except for the given set of users.

```
<target_audit_action_list> ::= 
   <target_audit_action_entry> [ [ EXCEPT ] <principal_list> ]
```


<dl>
<dt><b>

*<target\_audit\_action\_entry\>*

</b></dt>
<dd>

Only tables, views, procedures, and schemas can be specified.

```
<target_audit_action_entry> ::= 
   <target_audit_action_name> [ , <target_audit_action_name> [,...] ]
   ON <audit_object_name> [ , <audit_object_name> [,...] ]
```

In the case of *<schema\_name\>*.\*, all objects that are stored in this schema and can be combined with the specified *<target\_audit\_action\_name\>* values are audited. Synonyms and sequences cannot be selected as objects for audit policies. Only specified *<target\_audit\_action\_name\>* values can be combined with an object.



</dd><dt><b>

*<target\_audit\_action\_name\>*

</b></dt>
<dd>

```
<target_audit_action_name> ::= 
 { INSERT 
   | UPDATE 
   | DELETE 
   | SELECT 
   | EXECUTE }
```



</dd><dt><b>

*<audit\_object\_name\>*

</b></dt>
<dd>

```
<audit_object_name> ::= 
 { <table_name> 
   | <view_name> 
   | <procedure_name>
   | <schema_name>.}
```

```
<table_name> ::= [ <schema_name>.]<identifier>
```

```
<view_name> ::= [ <schema_name>.]<identifier>
```

```
<procedure_name> ::= [ <schema_name>.]<identifier>
```

```
<schema_name> ::= <unicode_name>
```

Specifies a database object for the target audit action.



</dd>
</dl>



</dd><dt><b>

*<schema\_audit\_action\_list\>*

</b></dt>
<dd>

```
<schema_audit_action_list> ::= <schema_audit_action_entry> [ [ EXCEPT ] FOR <user_name>[, <user_name> {,...] ] ]
```


<dl>
<dt><b>

*<schema\_audit\_action\_entry\>*

</b></dt>
<dd>

```
<schema_audit_action_entry> ::=
   <schema_audit_action_name>[, ...] 
   [ ON SCHEMA <audit_schema_name>[, <audit_schema_name> [,...] ] ]

```



</dd><dt><b>

*<schema\_audit\_action\_name\>*

</b></dt>
<dd>

```
<schema_audit_action_name> ::=
 { ALTER FUNCTION
   | ALTER INDEX
   | ALTER PROCEDURE
   | ALTER REMOTE SOURCE
   | ALTER REMOTE SUBSCRIPTION
   | ALTER SCHEDULER JOB
   | ALTER SEQUENCE
   | ALTER STRUCTURED FILTER
   | ALTER STRUCTURED PRIVILEGE
   | ALTER TABLE
   | ALTER VIEW
   | CREATE FUNCTION
   | CREATE GRAPH WORKSPACE
   | CREATE INDEX
   | CREATE PROCEDURE
   | CREATE REMOTE SOURCE
   | CREATE REMOTE SUBSCRIPTION
   | CREATE SCHEDULER JOB
   | CREATE SEQUENCE
   | CREATE STRUCTURED FILTER
   | CREATE STRUCTURED PRIVILEGE
   | CREATE SYNONYM
   | CREATE TABLE
   | CREATE TRIGGER
   | CREATE VIEW
   | DROP FUNCTION
   | DROP GRAPH WORKSPACE
   | DROP INDEX
   | DROP PROCEDURE
   | DROP REMOTE SOURCE
   | DROP REMOTE SUBSCRIPTION
   | DROP SCHEDULER JOB
   | DROP SEQUENCE
   | DROP STRUCTURED FILTER
   | DROP STRUCTURED PRIVILEGE
   | DROP SYNONYM
   | DROP TABLE
   | DROP TRIGGER
   | DROP VIEW
   | EXPORT
   | IMPORT
   | RENAME INDEX
   | RENAME TABLE }

```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<audit\_level\>*

</b></dt>
<dd>

Assigns an audit policy to an audit level.

```
<audit_level> ::= 
   { ERGENCY 
   | ALERT 
   | CRITICAL 
   | WARNING 
   | INFO }
```

The levels are listed above in decreasing order of importance.



</dd><dt><b>

*<opt\_audit\_trail\_type\>*

</b></dt>
<dd>

Specifies the audit trail target type\(s\) for the audit policy.

```
<opt_audit_trail_type> ::= TRAIL TYPE <audit_trail_type_list> 
```

```
<audit_trail_type_list> ::= <audit_trail_type_name> [, <audit_trail_type_name> [,...] ]
```

```
<audit_trail_type_name> ::=  
   { TABLE [ RETENTION <duration> ]
   | SYSLOG 
   | CSV }
```

```
<duration> ::= <integer>
```


<dl>
<dt><b>

RETENTION *<duration\>*

</b></dt>
<dd>

Specifies the length of time the policy is retained, expressed in days. A minimum allowed value can be configured with the configuration parameter \[auditing configuration\] minimal\_retention\_period. The default is 7 days.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d3d56075191014af43d6487fcaa603__sql_create_audit_policy_1sql_create_audit_policy_description"/>

## Description

The CREATE AUDIT POLICY statement creates a new audit policy, which monitors when specified audit actions occur. Only database users with the AUDIT ADMIN privilege can create an audit policy. An audit policy name must be unique.

New audit policies are disabled by default and must be enabled before the audit actions begin. The configuration parameter global\_auditing\_state must also be set to true.

An audit policy can contain only one of the following:

-   non-restricted auditing for n \(\>=1\) users
-   auditing for actions not restricted to objects
-   auditing for actions that are restricted to objects

For the last two alternatives listed, an optional restriction for user\(s\) is available.

**Audit Actions** 

One or more audit trail targets can be specified for an audit policy at the time of creation or after creation. The allowed audit trail targets are:

SYSLOG: uses the system syslog.

-   TABLE: stores audit information in database table. The audit log is accessible using AUDIT\_LOG system view.


<table>
<tr>
<th valign="top">

Audit Action Name

</th>
<th valign="top">

Group Number

</th>
<th valign="top">

Audit Operation

</th>
</tr>
<tr>
<td valign="top">

CANCEL SESSION

</td>
<td valign="top">

1 - Session Management and System Configuration

</td>
<td valign="top">

Audits the use of ALTER SYSTEM CANCEL SESSION statement to cancel a \(long\) running session

</td>
</tr>
<tr>
<td valign="top">

CONNECT

</td>
<td valign="top">

1 - Session Management and System Configuration

</td>
<td valign="top">

Audits the creation of a user connection to the database.

</td>
</tr>
<tr>
<td valign="top">

DISCONNECT SESSION

</td>
<td valign="top">

1 - Session Management and System Configuration

</td>
<td valign="top">

Audits the use of ALTER SYSTEM DISCONNECT SESSION to disconnect sessions.

</td>
</tr>
<tr>
<td valign="top">

STOP SERVICE

</td>
<td valign="top">

1 - Session Management and System Configuration

</td>
<td valign="top">

Audits the use of ALTER SYSTEM STOP SERVICE statement to stop a a particular database service process

</td>
</tr>
<tr>
<td valign="top">

SYSTEM CONFIGURATION CHANGE

</td>
<td valign="top">

1 - Session Management and System Configuration

</td>
<td valign="top">

Audits changes to the system configuration, such as the INIFILE.

</td>
</tr>
<tr>
<td valign="top">

VALIDATE USER

</td>
<td valign="top">

1 - Session Management and System Configuration

</td>
<td valign="top">

Audits the validation of a user's credentials.

</td>
</tr>
<tr>
<td valign="top">

GRANT ANY

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the granting of privileges and roles to users or roles.

</td>
</tr>
<tr>
<td valign="top">

GRANT PRIVILEGE

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the granting of privileges to users or roles.

</td>
</tr>
<tr>
<td valign="top">

GRANT ROLE

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the granting of roles to users or roles.

</td>
</tr>
<tr>
<td valign="top">

GRANT STRUCTURED PRIVILEGE

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the use of GRANT STRUCTURED PRIVILEGE statement to grant a structured privilege to a user or role

</td>
</tr>
<tr>
<td valign="top">

REVOKE ANY

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the revoking of privileges and roles from users or roles.

</td>
</tr>
<tr>
<td valign="top">

REVOKE PRIVILEGE

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the revoking of privileges from users or roles.

</td>
</tr>
<tr>
<td valign="top">

REVOKE ROLE

</td>
<td valign="top">

2 - Granting and Revoking of Authorization

</td>
<td valign="top">

Audits the revoking of roles from users or roles.

</td>
</tr>
<tr>
<td valign="top">

REVOKE STRUCTURED PRIVILEGE

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the use of REVOKE STRUCTURED PRIVILEGE statement to revoke a structured privilege from a user or role

</td>
</tr>
<tr>
<td valign="top">

DELETE

</td>
<td valign="top">

3 - Data Query and Manipulation

</td>
<td valign="top">

Audits the deletion of rows from tables/views and the truncation of tables. Requires the specification of target objects.

</td>
</tr>
<tr>
<td valign="top">

EXECUTE

</td>
<td valign="top">

3 - Data Query and Manipulation

</td>
<td valign="top">

Audits the execution of procedure calls. Requires the specification of target objects.

</td>
</tr>
<tr>
<td valign="top">

INSERT

</td>
<td valign="top">

3 - Data Query and Manipulation

</td>
<td valign="top">

Audits the use of INSERT/REPLACE/UPSERT statements on tables and views. Requires the specification of target objects.

</td>
</tr>
<tr>
<td valign="top">

SELECT

</td>
<td valign="top">

3 - Data Query and Manipulation

</td>
<td valign="top">

Audits the use of SELECT statements on tables and views. Requires specification of target objects.

</td>
</tr>
<tr>
<td valign="top">

UPDATE

</td>
<td valign="top">

3 - Data Query and Manipulation

</td>
<td valign="top">

Audits the use of UPDATE/REPLACE/UPSERT statements on tables and views. Requires specification of target objects.

</td>
</tr>
<tr>
<td valign="top">

ALTER ROLE

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the alteration of roles.

</td>
</tr>
<tr>
<td valign="top">

ALTER ROLEGROUP

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the alteration of role groups.

</td>
</tr>
<tr>
<td valign="top">

ALTER USER

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the alteration of users.

</td>
</tr>
<tr>
<td valign="top">

ALTER USERGROUP

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the alteration of user groups.

</td>
</tr>
<tr>
<td valign="top">

CREATE ROLE

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the creation of roles.

</td>
</tr>
<tr>
<td valign="top">

CREATE ROLEGROUP

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the use of CREATE ROLEGROUP statement to create a role group

</td>
</tr>
<tr>
<td valign="top">

CREATE USER

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the creation of users.

</td>
</tr>
<tr>
<td valign="top">

CREATE USERGROUP

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the creation of user groups.

</td>
</tr>
<tr>
<td valign="top">

DROP ROLE

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the dropping of roles.

</td>
</tr>
<tr>
<td valign="top">

DROP ROLEGROUP

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the use of DROP ROLEGROUP statement to drop an existing role group

</td>
</tr>
<tr>
<td valign="top">

DROP USER

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the dropping of users.

</td>
</tr>
<tr>
<td valign="top">

DROP USERGROUP

</td>
<td valign="top">

4 - User and Role Management

</td>
<td valign="top">

Audits the dropping of user groups.

</td>
</tr>
<tr>
<td valign="top">

ALTER STRUCTURED PRIVILEGE

</td>
<td valign="top">

7 - Structured Privilege Management

</td>
<td valign="top">

Audits the use of ALTER STRUCTURED PRIVILEGE statement to change the current definition of an existing structured privilege

</td>
</tr>
<tr>
<td valign="top">

CREATE STRUCTURED PRIVILEGE

</td>
<td valign="top">

7 - Structured Privilege Management

</td>
<td valign="top">

Audits the use of CREATE STRUCTURED PRIVILEGE statement to create a new structured privilege

</td>
</tr>
<tr>
<td valign="top">

DROP STRUCTURED PRIVILEGE

</td>
<td valign="top">

7 - Structured Privilege Management

</td>
<td valign="top">

Audits the use of DROP STRUCTURED PRIVILEGE statement to drop an existing structured privilege

</td>
</tr>
<tr>
<td valign="top">

SET SYSTEM LICENSE

</td>
<td valign="top">

9 - License Deletion

</td>
<td valign="top">

Audits the use of SET SYSTEM LICENSE statement to install a new license key in the current database \(SYSTEMDB or Tenant DB\)

</td>
</tr>
<tr>
<td valign="top">

UNSET SYSTEM LICENSE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of UNSET SYSTEM LICENSE statement to delete all existing license keys in the current database \(SYSTEMDB or Tenant DB\)

</td>
</tr>
<tr>
<td valign="top">

ALTER FUNCTION

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of functions.

</td>
</tr>
<tr>
<td valign="top">

ALTER INDEX

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of indexes.

</td>
</tr>
<tr>
<td valign="top">

ALTER PROCEDURE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of procedures.

</td>
</tr>
<tr>
<td valign="top">

ALTER SCHEDULER JOB

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of ALTER SCHEDULER JOB statement to change the definition of an existing scheduler job

</td>
</tr>
<tr>
<td valign="top">

ALTER SEQUENCE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of sequences.

</td>
</tr>
<tr>
<td valign="top">

ALTER STATISTICS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of statistics.

</td>
</tr>
<tr>
<td valign="top">

ALTER TABLE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of tables.

</td>
</tr>
<tr>
<td valign="top">

ALTER TENANT

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of ALTER TENANT statement to change the definition of an existing tenant

</td>
</tr>
<tr>
<td valign="top">

ALTER VIEW

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of views.

</td>
</tr>
<tr>
<td valign="top">

ALTER WORKLOAD CLASS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of workload classes.

</td>
</tr>
<tr>
<td valign="top">

ALTER WORKLOAD MAPPING

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the alteration of workload mappings.

</td>
</tr>
<tr>
<td valign="top">

CREATE FUNCTION

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of functions.

</td>
</tr>
<tr>
<td valign="top">

CREATE GRAPH WORKSPACE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of graph workspaces.

</td>
</tr>
<tr>
<td valign="top">

CREATE INDEX

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of indexes.

</td>
</tr>
<tr>
<td valign="top">

CREATE PROCEDURE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of procedures.

</td>
</tr>
<tr>
<td valign="top">

CREATE SCHEDULER JOB

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of CREATE SCHEDULER JOB statement to create a new scheduler job

</td>
</tr>
<tr>
<td valign="top">

CREATE SCHEMA

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of schemas.

</td>
</tr>
<tr>
<td valign="top">

CREATE SEQUENCE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of sequences.

</td>
</tr>
<tr>
<td valign="top">

CREATE STATISTICS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of statistics.

</td>
</tr>
<tr>
<td valign="top">

CREATE SYNONYM

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of synonyms.

</td>
</tr>
<tr>
<td valign="top">

CREATE TABLE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of tables.

</td>
</tr>
<tr>
<td valign="top">

CREATE TENANT

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of CREATE TENANT statement to create a new TENANT

</td>
</tr>
<tr>
<td valign="top">

CREATE TRIGGER

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of triggers.

</td>
</tr>
<tr>
<td valign="top">

CREATE VIEW

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of views.

</td>
</tr>
<tr>
<td valign="top">

CREATE WORKLOAD CLASS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of workload classes.

</td>
</tr>
<tr>
<td valign="top">

CREATE WORKLOAD MAPPING

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the creation of workload mappings.

</td>
</tr>
<tr>
<td valign="top">

DROP FUNCTION

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of functions.

</td>
</tr>
<tr>
<td valign="top">

DROP GRAPH WORKSPACE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of graph workspaces.

</td>
</tr>
<tr>
<td valign="top">

DROP INDEX

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of indexes.

</td>
</tr>
<tr>
<td valign="top">

DROP PROCEDURE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of procedures.

</td>
</tr>
<tr>
<td valign="top">

DROP SCHEDULER JOB

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of DROP SCHEDULER JOB statement to drop an existing scheduler job

</td>
</tr>
<tr>
<td valign="top">

DROP SCHEMA

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of schemas.

</td>
</tr>
<tr>
<td valign="top">

DROP SEQUENCE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of sequences.

</td>
</tr>
<tr>
<td valign="top">

DROP STATISTICS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of statistics.

</td>
</tr>
<tr>
<td valign="top">

DROP SYNONYM

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of synonymns.

</td>
</tr>
<tr>
<td valign="top">

DROP TABLE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of tables.

</td>
</tr>
<tr>
<td valign="top">

DROP TENANT

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the use of DROP TENANT statement to drop an existing tenant

</td>
</tr>
<tr>
<td valign="top">

DROP TRIGGER

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of triggers.

</td>
</tr>
<tr>
<td valign="top">

DROP VIEW

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of views.

</td>
</tr>
<tr>
<td valign="top">

DROP WORKLOAD CLASS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of workload classes.

</td>
</tr>
<tr>
<td valign="top">

DROP WORKLOAD MAPPING

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the dropping of workload mappings.

</td>
</tr>
<tr>
<td valign="top">

REFRESH STATISTICS

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the refreshing of statistics.

</td>
</tr>
<tr>
<td valign="top">

RENAME COLUMN

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the renaming of columns

</td>
</tr>
<tr>
<td valign="top">

RENAME INDEX

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the renaming of indexes

</td>
</tr>
<tr>
<td valign="top">

RENAME TABLE

</td>
<td valign="top">

11 - Data Definition

</td>
<td valign="top">

Audits the renaming of tables

</td>
</tr>
<tr>
<td valign="top">

BACKUP CATALOG DELETE

</td>
<td valign="top">

13 - Backup and Recovery

</td>
<td valign="top">

Audits the deletion of the backed up catalog

</td>
</tr>
<tr>
<td valign="top">

BACKUP DATA

</td>
<td valign="top">

13 - Backup and Recovery

</td>
<td valign="top">

Audits the backup up of data

</td>
</tr>
<tr>
<td valign="top">

RECOVER DATA

</td>
<td valign="top">

13 - Backup and Recovery

</td>
<td valign="top">

Audits the recovery of data

</td>
</tr>
<tr>
<td valign="top">

ACTIVATE KEY MANAGEMENT CONFIGURATION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER SYSTEM ACTIVATE KEY MANAGEMENT CONFIGURATION to activate a configuration in external key management

</td>
</tr>
<tr>
<td valign="top">

ADD KEY MANAGEMENT CONFIGURATION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER SYSTEM ADD KEY MANAGEMENT CONFIGURATION to add a new configuration to external key management

</td>
</tr>
<tr>
<td valign="top">

ALTER APPLICATION ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of application encryption keys.

</td>
</tr>
<tr>
<td valign="top">

ALTER APPLICATION ENCRYPTION ROOT KEY

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of application encryption root keys.

</td>
</tr>
<tr>
<td valign="top">

ALTER BACKUP ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER SYSTEM BACKUP ENCRYPTION to specify backup encryption options

</td>
</tr>
<tr>
<td valign="top">

ALTER BACKUP ENCRYPTION ROOT KEY

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER SYSTEM BACKUP ENCRYPTION CREATE NEW ROOT KEY statement to create a new root key for backup encryption

</td>
</tr>
<tr>
<td valign="top">

ALTER KEY MANAGEMENT CONFIGURATION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER SYSTEM ALTER KEY MANAGEMENT CONFIGURATION statement to change an existing configuration in external key management

</td>
</tr>
<tr>
<td valign="top">

ALTER LOG ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of log encryption status.

</td>
</tr>
<tr>
<td valign="top">

ALTER LOG ENCRYPTION ROOT KEY

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of log encryption root keys.

</td>
</tr>
<tr>
<td valign="top">

ALTER PERSISTENCE ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of database persistence encryption status and page encryption keys.

</td>
</tr>
<tr>
<td valign="top">

ALTER PERSISTENCE ENCRYPTION ROOT KEY

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Altering database persistence encryption root keys.

</td>
</tr>
<tr>
<td valign="top">

ALTER ROOT KEYS BACKUP PASSWORD

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of the backup password used to protect backup root keys.

</td>
</tr>
<tr>
<td valign="top">

DROP KEY MANAGEMENT CONFIGURATION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER SYSTEM DROP KEY MANAGEMENT CONFIGURATION statement to drop an existing configuration in external key management

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION CONFIG CONTROL

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the alteration of the database \(system or local tenant database\) controlling the encryption configuration.

</td>
</tr>
<tr>
<td valign="top">

TENANT BACKUP ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the use of ALTER DATABASE BACKUP ENCRYPTION \[ON|OFF\] statements to switch backup encryption on or off for this database

</td>
</tr>
<tr>
<td valign="top">

TENANT LOG ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the switching on or off of the log encryption for the tenant.

</td>
</tr>
<tr>
<td valign="top">

TENANT PERSISTENCE ENCRYPTION

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the switching on or off of the data volume encryption for the tenant.

</td>
</tr>
<tr>
<td valign="top">

TENANT ROOT KEYS BACKUP PASSWORD

</td>
<td valign="top">

14 - Volume Encryption

</td>
<td valign="top">

Audits the setting the root key backup password.

</td>
</tr>
<tr>
<td valign="top">

ALTER ADAPTER

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the alteration of adapters.

</td>
</tr>
<tr>
<td valign="top">

ALTER AGENT

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the alteration of agents.

</td>
</tr>
<tr>
<td valign="top">

ALTER REMOTE SOURCE

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the alteration of remote sources.

</td>
</tr>
<tr>
<td valign="top">

ALTER REMOTE SUBSCRIPTION

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the alteration of remote subscriptions.

</td>
</tr>
<tr>
<td valign="top">

CREATE ADAPTER

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the creation of adapters.

</td>
</tr>
<tr>
<td valign="top">

CREATE AGENT

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the creation of agents.

</td>
</tr>
<tr>
<td valign="top">

CREATE AGENT GROUP

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the creation of agent groups.

</td>
</tr>
<tr>
<td valign="top">

CREATE REMOTE SOURCE

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the creation of remote sources.

</td>
</tr>
<tr>
<td valign="top">

CREATE REMOTE SUBSCRIPTION

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the creation of remote subscriptions.

</td>
</tr>
<tr>
<td valign="top">

DROP ADAPTER

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the dropping of adapters.

</td>
</tr>
<tr>
<td valign="top">

DROP AGENT

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the dropping of agents.

</td>
</tr>
<tr>
<td valign="top">

DROP AGENT GROUP

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the dropping of agent groups.

</td>
</tr>
<tr>
<td valign="top">

DROP REMOTE SOURCE

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the dropping of remote sources.

</td>
</tr>
<tr>
<td valign="top">

DROP REMOTE SUBSCRIPTION

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the dropping of remote subscriptions.

</td>
</tr>
<tr>
<td valign="top">

PROCESS REMOTE SUBSCRIPTION EXCEPTION

</td>
<td valign="top">

17 - Data Provisioning

</td>
<td valign="top">

Audits the processing of remote subscription exceptions.

</td>
</tr>
<tr>
<td valign="top">

ALTER PSE

</td>
<td valign="top">

19 - Certificates and PSE Store

</td>
<td valign="top">

Audits the alteration of PSEs.

</td>
</tr>
<tr>
<td valign="top">

CREATE CERTIFICATE

</td>
<td valign="top">

19 - Certificates and PSE Store

</td>
<td valign="top">

Audits the creation of certificates.

</td>
</tr>
<tr>
<td valign="top">

CREATE PSE

</td>
<td valign="top">

19 - Certificates and PSE Store

</td>
<td valign="top">

Audits the creation of PSEs.

</td>
</tr>
<tr>
<td valign="top">

CREATE PUBLIC KEY

</td>
<td valign="top">

19 - Certificates and PSE store

</td>
<td valign="top">

Audits the use of CREATE PUBLIC KEY statement to create a new public key

</td>
</tr>
<tr>
<td valign="top">

DROP CERTIFICATE

</td>
<td valign="top">

19 - Certificates and PSE Store

</td>
<td valign="top">

Audits the dropping of certificates.

</td>
</tr>
<tr>
<td valign="top">

DROP PSE

</td>
<td valign="top">

19 - Certificates and PSE Store

</td>
<td valign="top">

Audits the dropping of PSEs.

</td>
</tr>
<tr>
<td valign="top">

DROP PUBLIC KEY

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the use of DROP PUBLIC KEY statement to drop an existing public key

</td>
</tr>
<tr>
<td valign="top">

ALTER JWT PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the alteration of JWT providers.

</td>
</tr>
<tr>
<td valign="top">

ALTER LDAP PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the alteration of LDAP providers.

</td>
</tr>
<tr>
<td valign="top">

ALTER SAML PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the alteration of SAML providers.

</td>
</tr>
<tr>
<td valign="top">

ALTER X509 PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the use of ALTER X509 PROVIDER statement to change the definition of an existing X509 provider

</td>
</tr>
<tr>
<td valign="top">

CREATE JWT PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the creation of JWT providers.

</td>
</tr>
<tr>
<td valign="top">

CREATE LDAP PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the creation of LDAP providers.

</td>
</tr>
<tr>
<td valign="top">

CREATE SAML PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the creation of SAML providers.

</td>
</tr>
<tr>
<td valign="top">

CREATE X509 PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the use of CREATE X509 PROVIDER statement to create a new X509 provider

</td>
</tr>
<tr>
<td valign="top">

DROP JWT PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the dropping of JWT providers.

</td>
</tr>
<tr>
<td valign="top">

DROP LDAP PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the dropping of LDAP providers.

</td>
</tr>
<tr>
<td valign="top">

DROP SAML PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the dropping of SAML providers.

</td>
</tr>
<tr>
<td valign="top">

DROP X509 PROVIDER

</td>
<td valign="top">

Authentication Provider Management

</td>
<td valign="top">

Audits the use of DROP X509 PROVIDER statement to drop an existing X509 provider

</td>
</tr>
<tr>
<td valign="top">

VALIDATE LDAP PROVIDER

</td>
<td valign="top">

20 - Authentication Provider Management

</td>
<td valign="top">

Audits the refreshing of LDAP providers.

</td>
</tr>
<tr>
<td valign="top">

DEBUGGER ATTACH PROCESS

</td>
<td valign="top">

23 - Procedure Debugging

</td>
<td valign="top">

Audits audit log debugger attachment process events.

</td>
</tr>
<tr>
<td valign="top">

DEBUGGER EXECUTION

</td>
<td valign="top">

23 - Procedure Debugging

</td>
<td valign="top">

Audits audit log debugger execution events.

</td>
</tr>
<tr>
<td valign="top">

CREATE CREDENTIAL

</td>
<td valign="top">

24 - Credential Management

</td>
<td valign="top">

Audits the creation of a credential.

</td>
</tr>
<tr>
<td valign="top">

ALTER CREDENTIAL

</td>
<td valign="top">

24 - Credential Management

</td>
<td valign="top">

Audits the alteration of a credential.

</td>
</tr>
<tr>
<td valign="top">

DROP CREDENTIAL

</td>
<td valign="top">

24 - Credential Management

</td>
<td valign="top">

Audits the dropping of a credential.

</td>
</tr>
<tr>
<td valign="top">

EXPORT

</td>
<td valign="top">

25 - Data Import Export

</td>
<td valign="top">

Audits the export of data

</td>
</tr>
<tr>
<td valign="top">

IMPORT

</td>
<td valign="top">

25 - Data Import Export

</td>
<td valign="top">

Audits the import of data

</td>
</tr>
<tr>
<td valign="top">

IMPORT SCAN

</td>
<td valign="top">

25 - Data Import Export

</td>
<td valign="top">

Audits the scan of import data

</td>
</tr>
<tr>
<td valign="top">

CREATE STRUCTURED FILTER

</td>
<td valign="top">

26 - Structured Filter Management

</td>
<td valign="top">

Audits the creation of a structured privilege

</td>
</tr>
<tr>
<td valign="top">

ALTER STRUCTURED FILTER

</td>
<td valign="top">

26 - Structured Filter Management

</td>
<td valign="top">

Audits the alteration of a structured privilege

</td>
</tr>
<tr>
<td valign="top">

DROP STRUCTURED FILTER

</td>
<td valign="top">

26 - Structured Filter Management

</td>
<td valign="top">

Audits the dropping of a structured privilege

</td>
</tr>
</table>



<a name="loio20d3d56075191014af43d6487fcaa603__section_snl_sp5_qbb"/>

## Permissions

You must have the AUDIT ADMIN system privilege to create an audit policy.



<a name="loio20d3d56075191014af43d6487fcaa603__sql_create_audit_policy_1sql_create_audit_policy_examples"/>

## Example

Create a new audit policy named priv\_audit that audits successful granting and revoking of privileges and roles. The audit policy has the medium audit level CRITICAL.

This policy has to be explicitly enabled to cause the auditing of the audit policy.

```
CREATE AUDIT POLICY priv_audit AUDITING SUCCESSFUL GRANT PRIVILEGE, REVOKE PRIVILEGE, GRANT ROLE, REVOKE ROLE LEVEL CRITICAL;
```

Create a new audit policy named object\_audit that audits the inserts into the existing table MY\_SCHEMA.MY\_TABLE. This policy must be explicitly enabled to cause the auditing of the audit policy. This policy is restricted to user FRED and uses the audit level INFO.

```
CREATE USER FRED PASSWORD <pwd>;
 CREATE SCHEMA MY_SCHEMA OWNED BY system;
 CREATE ROW TABLE MY_SCHEMA.MY_TABLE (first_col int);
 GRANT INSERT ON MY_SCHEMA.MY_TABLE to FRED;
 CREATE AUDIT POLICY OBJECT_AUDIT AUDITING SUCCESSFUL INSERT ON MY_SCHEMA.MY_TABLE FOR FRED LEVEL INFO;
```

Create a new audit policy named update\_object\_audit that audits the updates of the existing table MY\_SCHEMA.MY\_TABLE. This policy must be enabled explicitly to make the auditing of the audit policy occur. The auditing should be done for all users except the existing user TECH\_ADMIN. This policy uses the audit level CRITICAL.

```
CREATE USER TECH_ADMIN PASSWORD <pwd>;
 CREATE SCHEMA MY_SCHEMA OWNED BY system;
 CREATE ROW TABLE MY_SCHEMA.MY_TABLE (first_col int);
 GRANT UPDATE ON MY_SCHEMA.MY_TABLE to TECH_ADMIN;
 CREATE AUDIT POLICY UPDATE_OBJECT_AUDIT AUDITING SUCCESSFUL UPDATE ON MY_SCHEMA.MY_TABLE EXCEPT FOR TECH_ADMIN LEVEL CRITICAL;
```

Create an audit policy that tracks all tables created in the schema TEST\_SCHEMA.

```
CREATE AUDIT POLICY MY_AUDIT_POLICY AUDITING ALL CREATE TABLE ON SCHEMA TEST_SCHEMA LEVEL INFO;
```

**Related Information**  


[AUDIT\_POLICIES System View](../../020-System-Views-Reference/021-System-Views/audit-policies-system-view-209e4d3.md "Provides information about audit policies.")

[ALTER AUDIT POLICY Statement \(Access Control\)](alter-audit-policy-statement-access-control-20cfb7b.md "Enables or disables an audit policy, changes audit trail target types for an audit policy, and configures the retention period of the policy.")

[Auditing](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/ddcb6ed2bb5710148183db80e4aca49b.html "Auditing allows you to monitor and record selected actions performed in the SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

[AUDIT\_ACTIONS System View](../../020-System-Views-Reference/021-System-Views/audit-actions-system-view-b856cdd.md "Provides information about all available audit actions.")

