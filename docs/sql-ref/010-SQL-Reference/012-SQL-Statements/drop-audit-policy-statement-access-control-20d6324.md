<!-- loio20d6324675191014b588d13fe491415e -->

# DROP AUDIT POLICY Statement \(Access Control\)

Drops an audit policy.



<a name="loio20d6324675191014b588d13fe491415e__sql_drop_audit_policy_1sql_drop_audit_policy_syntax"/>

## Syntax

```
DROP AUDIT POLICY <policy_name>
```



<a name="loio20d6324675191014b588d13fe491415e__sql_drop_audit_policy_1sql_drop_audit_policy_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<policy\_name\>*

</b></dt>
<dd>

Specifies the name of the audit policy to be dropped.

```
<policy_name> ::= <identifier>
```

*<policy\_name\>* must specify an existing audit policy.



</dd>
</dl>



<a name="loio20d6324675191014b588d13fe491415e__sql_drop_audit_policy_1sql_drop_audit_policy_description"/>

## Description

Even if an audit policy is dropped, the audit action specified in the dropped audit policy can be audited further. This happens if another audit policy is enabled that specifies the dropped audit action.

To temporarily stop auditing an audit policy, disable it.

Since there is no automatic deletion of audit log entries for deleted policies, audit log entries created by such a policy need to be cleaned up manually.



<a name="loio20d6324675191014b588d13fe491415e__section_snl_sp5_qbb"/>

## Permissions

To drop an audit policy, you must have the AUDIT ADMIN system privilege.



<a name="loio20d6324675191014b588d13fe491415e__sql_drop_audit_policy_1sql_drop_audit_policy_examples"/>

## Example

Create the priv\_audit audit policy.

```
CREATE AUDIT POLICY priv_audit AUDITING SUCCESSFUL GRANT PRIVILEGE, REVOKE PRIVILEGE, GRANT ROLE, REVOKE ROLE LEVEL CRITICAL;
```

Drop the priv\_audit audit policy.

```
DROP AUDIT POLICY priv_audit;
```

**Related Information**  


[AUDIT\_POLICIES System View](../../020-System-Views-Reference/021-System-Views/audit-policies-system-view-209e4d3.md "Provides information about audit policies.")

[Auditing](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/ddcb6ed2bb5710148183db80e4aca49b.html "Auditing allows you to monitor and record selected actions performed in the SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

