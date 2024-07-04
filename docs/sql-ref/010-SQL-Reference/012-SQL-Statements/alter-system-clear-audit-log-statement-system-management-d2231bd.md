<!-- loiod2231bd2d2951014ad35d218ea6628c8 -->

# ALTER SYSTEM CLEAR AUDIT LOG Statement \(System Management\)

Deletes old audit data from the SAP HANA database audit table.



<a name="loiod2231bd2d2951014ad35d218ea6628c8__sql_alter_clear_audit_log_1sql_alter_system_clear_audit_log"/>

## Syntax

```
ALTER SYSTEM CLEAR AUDIT LOG [ FOR AUDIT POLICY <policy_name> ] <until_specification>
```



<a name="loiod2231bd2d2951014ad35d218ea6628c8__sql_function_score_1xyz_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<until\_specification\>*

</b></dt>
<dd>

Removes audit data older than the *<timestamp\>*.

```
<until_specification> ::= { UNTIL <timestamp> | ALL }

<timestamp> ::= <string_literal>
```

If the ALL keyword is used, then all the audit data is removed.



</dd>
</dl>



<a name="loiod2231bd2d2951014ad35d218ea6628c8__sql_alter_clear_audit_log_1sql_alter_system_clear_audit_log_description"/>

## Description

Use this command to delete old audit data from the SAP HANA database audit table.



<a name="loiod2231bd2d2951014ad35d218ea6628c8__section_if2_5tc_pbb"/>

## Permissions

You must have the system privilege AUDIT OPERATOR to clear the audit log.



<a name="loiod2231bd2d2951014ad35d218ea6628c8__sql_alter_clear_audit_log_1sql_alter_system_clear_audit_log_examples"/>

## Example

Delete audit log data older than December 31st 2012.

```
ALTER SYSTEM CLEAR AUDIT LOG UNTIL '2012-12-31 23:59:59';
```

Delete all audit log data for audit policy MY\_POLICY.

```
ALTER SYSTEM CLEAR AUDIT LOG FOR AUDIT POLICY MY_POLICY ALL;
```

**Related Information**  


[Audit Trail](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/db560e7bbb57101490d4a1364440077f.html "When an audit policy is triggered, that is, when an action in the policy occurs under the conditions defined in the policy, an audit entry is created in the audit trail.") :arrow_upper_right:

[AUDIT\_LOG System View](../../020-System-Views-Reference/021-System-Views/audit-log-system-view-d1fe124.md "Provides information about audit records, with the exception of XSA-auditing.")

