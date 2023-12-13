<!-- loio20cfb7b875191014866c930164aaf07c -->

# ALTER AUDIT POLICY Statement \(Access Control\)

Enables or disables an audit policy, changes audit trail target types for an audit policy, and configures the retention period of the policy.



<a name="loio20cfb7b875191014866c930164aaf07c__sql_alter_audit_policy_1sql_alter_audit_policy_syntax"/>

## Syntax

```
ALTER AUDIT POLICY <policy_name> 
{ <audit_mode> 
   | <set_audit_trail_type>
   | <reset_audit_trail_type> 
   | <set_audit_trail_retention>
   | <reset_audit_trail_retention>}
```



<a name="loio20cfb7b875191014866c930164aaf07c__sql_alter_audit_policy_1sql_alter_audit_policy_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<policy\_name\>*

</b></dt>
<dd>

Specifies the name of the audit policy to be altered.

```
<policy_name> ::= <identifier>
```



</dd><dt><b>

*<audit\_mode\>*

</b></dt>
<dd>

Enables or disables the audit policy.

```
<audit_mode> ::= ENABLE | DISABLE
```


<dl>
<dt><b>

ENABLE

</b></dt>
<dd>

Enables the audit policy.



</dd><dt><b>

DISABLE

</b></dt>
<dd>

Disables the audit policy.



</dd>
</dl>



</dd><dt><b>

*<set\_audit\_trail\_type\>*

</b></dt>
<dd>

Specifies the audit trail target types for the audit policy.

```
<set_audit_trail_types> ::= SET TRAIL TYPE <audit_trail_type_list>

<audit_trail_type_list> ::= <audit_trail_type_name> [, <audit_trail_type_name> [,...] ]

<audit_trail_type_name> ::= 
 TABLE  [ RETENTION <duration> ]
 | SYSLOG 
 | CSV
```

Specifying CSV on a production system has security implications: users with the CATALOG READ, TRACE ADMIN, or INIFILE ADMIN privilege are able to access the CSV file.


<dl>
<dt><b>

*<duration\>*

</b></dt>
<dd>

Specifies the length of time the policy is retained, expressed in days. The value specified in the CREATE or ALTER AUDIT POLICY statement must be greater than the value specified for the minimal\_retention\_period parameter in the auditing configuration section of the global.ini file. An error is generated if the value is less. The minimal\_retention\_period parameter value must be between 7 and 3653 \(10 years\). This limitation does not apply to the duration value in the CREATE or ALTER AUDIT POLICY statement.



</dd>
</dl>



</dd><dt><b>

*<reset\_audit\_trail\_type\>*

</b></dt>
<dd>

Resets the audit trail target type\(s\) to the system default.

```
<reset_audit_trail_type> ::= RESET TRAIL TYPE
```



</dd><dt><b>

*<set\_audit\_trail\_retention\>*

</b></dt>
<dd>

Specifies the length of time the audit entries are retained.

```
<set_audit_trail_retention> ::= SET RETENTION <duration>
```



</dd><dt><b>

*<reset\_audit\_trail\_retention\>*

</b></dt>
<dd>

Resets the audit trail retention period to the default, which is forever.

```
<reset_audit_trail_retention> ::= RESET RETENTION
```



</dd>
</dl>

> ### Note:  
> If the retention period is changed, any audit entries that are no longer included are deleted immediately.



<a name="loio20cfb7b875191014866c930164aaf07c__sql_alter_audit_policy_1sql_alter_audit_policy_description"/>

## Description

The ALTER AUDIT POLICY statement enables or disables an audit policy. *<policy\_name\>* must specify an existing audit policy. Only database users with the AUDIT ADMIN privilege are allowed to alter an audit policy. Users with this privilege can alter any audit policy, regardless of if they are the creator of the policy.

New audit policies are disabled by default and must be enabled before the audit actions begin. The configuration parameter global\_auditing\_state must also be set to true.

An audit policy can be disabled and enabled as often as required.

Specify one or more audit trail targets for an audit policy at the time of creation. The allowed audit trail targets are:

-   SYSLOG: uses the system syslog.
-   TABLE: stores audit information in database table. The audit log is accessible using AUDIT\_LOG system view.
-   CSV: stores audit information as comma-separated values in a text file. Use only for testing purposes.



<a name="loio20cfb7b875191014866c930164aaf07c__section_snl_sp5_qbb"/>

## Permissions

You must have the AUDIT ADMIN system privilege to alter an audit policy.



<a name="loio20cfb7b875191014866c930164aaf07c__sql_alter_audit_policy_1sql_alter_audit_policy_examples"/>

## Example

Create an audit policy called priv\_audit by using the following statement.

```
CREATE AUDIT POLICY "priv_audit"
   AUDITING SUCCESSFUL
   GRANT PRIVILEGE, REVOKE PRIVILEGE, GRANT ROLE, REVOKE ROLE LEVEL CRITICAL;
```

Enable the priv\_audit audit policy.

```
ALTER AUDIT POLICY "priv_audit" ENABLE;
```

Set SYSLOG and TABLE as audit trail targets for the priv\_audit audit policy.

```
ALTER AUDIT POLICY "priv_audit" SET TRAIL TYPE SYSLOG, TABLE;
```

Reset audit trail targets for the priv\_audit audit policy.

```
ALTER AUDIT POLICY "priv_audit" RESET TRAIL TYPE;
```

Disable the priv\_audit audit policy.

```
ALTER AUDIT POLICY "priv_audit" DISABLE;
```

Set the retention period for the priv\_audit policy to 30 days.

```
ALTER AUDIT POLICY "priv_audit" SET RETENTION 30;
```

Remove the retention period for the priv\_audit policy.

```
ALTER AUDIT POLICY "priv_audit" RESET RETENTION;
```

**Related Information**  


[AUDIT\_POLICIES System View](../../020-System-Views-Reference/021-System-Views/audit-policies-system-view-209e4d3.md "Provides information about audit policies.")

[CREATE AUDIT POLICY Statement \(Access Control\)](create-audit-policy-statement-access-control-20d3d56.md "Creates an audit policy.")

[Auditing](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/ddcb6ed2bb5710148183db80e4aca49b.html "Auditing allows you to monitor and record selected actions performed in the SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

[M\_INIFILE\_CONTENTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifile-contents-system-view-20b16a7.md "Provides configuration information from INI files.")

[AUDIT\_LOG System View](../../020-System-Views-Reference/021-System-Views/audit-log-system-view-d1fe124.md "Provides information about audit records, with the exception of XSA-auditing.")

