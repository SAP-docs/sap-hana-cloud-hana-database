<!-- loio0bd8fc152db14c798c16b82acf2024ae -->

# Security-relevant Logging and Tracing in SAP HDI

The auditing process enables you to trace who has performed which kinds of operations in the context of SAP HDI.

System audit logs can help detect undesired modifications that have security implications, for example, changes to user authorization, creation and deletion of database objects, or changes to the system configuration. Audit logs can also help uncover attempts to breach system security or reveal security holes, for example, where a specific user has privileges that are not necessary. Auditing can also help protect the system owner against the threat of security violations and data misuse or may serve to meet security standards of a company. For SAP HDI auditing, audit-log events can be written to SAP HANA's central auditing service.



<a name="loio0bd8fc152db14c798c16b82acf2024ae__section_sct_2t4_4gb"/>

## Activating Auditing in SAP HANA

To use the auditing feature in productive SAP HANA systems, it must first be activated, for example, by adding an entry to a system configuration file or by executing the following SQL command with the system privilege “`AUDIT ADMIN`”:

```sql
alter system alter configuration ('global.ini', 'SYSTEM') set ('auditing 
configuration', 'global_auditing_state') = 'true' with reconfigure;
```

You define an audit policy by declaring the actions or operations that you want to trigger an entry in the audit report as well as the conditions under which the actions must be performed. For example, the following SQL command shows how to create an audit policy that checks on all “`create user`” or “`drop user`” operations, writes an entry to the audit log with the severity level “`critical`”:

```sql
create audit policy TEST_AUDIT_POLICY
auditing all     
create user, drop user
level critical;
```

In an SAP HANA SQL audit policy, `auditing all` refers to the status of the audited action or operation, for example, "successful", "unsuccessful", or "all". The `level` specifies the severity status assigned to the entries logged by the audit policy for the corresponding actions, in this example, `create user` and `drop user`. You create a new policy for each groups of actions to which you want to assign a different severity level, for example: `info`, `warning`, `critical`, or `alert`.

After creation, an audit policy must be activated, for example, with the following SQL command:

```sql
alter audit policy TEST_AUDIT_POLICY enable;
```

For more information audit policies, see the `CREATE AUDIT POLICY` command in the *SAP HANA SQL and System Views Reference for SAP HANA Platform*.



<a name="loio0bd8fc152db14c798c16b82acf2024ae__section_ccq_kmg_4gb"/>

## Auditing in SAP HDI

The standard capabilities provided by the SAP HANA audit policies are sufficient for auditing actions in the context of SAP HDI, too. The functionality of SAP HDI is provided by means of an SQL interface and implemented either as built-in procedures or stored procedures. Using the existing auditing features, it is possible to audit all calls to SAP HDI.



<a name="loio0bd8fc152db14c798c16b82acf2024ae__section_dfs_vmg_4gb"/>

## Auditing SAP HDI Procedures

In SAP HDI, general procedures enable the execution of high-level operations, for example, creating and dropping containers, granting and revoking privileges and roles, or configuring SAP HDI itself. The following code example shows how to use SQL to create and enable an audit policy that audits these general SAP HDI procedures:The standard capabilities provided by the SAP HANA auditing mechanism are sufficient for auditing in SAP HDI, too. The functionality of SAP HDI is provided by means of an SQL interface and implemented either as built-in procedures or stored procedures. Using the existing auditing features, it is possible to audit all calls to SAP HDI.

> ### Sample Code:  
> Creating a General Audit Policy
> 
> ```sql
> create audit policy TEST_AUDIT_POLICY_HDI
> auditing all
> execute on
> _SYS_DI.CONFIGURE_DI_PARAMETERS,
> _SYS_DI.CREATE_CONTAINER_GROUP,
> _SYS_DI.DROP_CONTAINER_GROUP,
> _SYS_DI.GRANT_CONTAINER_GROUP_API_PRIVILEGES,
> _SYS_DI.GRANT_CONTAINER_GROUP_API_PRIVILEGES_WITH_GRANT_OPTION,
> _SYS_DI.GRANT_DI_SUPPORT_PRIVILEGE,
> _SYS_DI.LIST_LIBRARIES,
> _SYS_DI.MOVE_CONTAINER_TO_GROUP,
> _SYS_DI.REVOKE_CONTAINER_GROUP_API_PRIVILEGES,
> _SYS_DI.REVOKE_DI_SUPPORT_PRIVILEGE,
> level info;
> 
> alter audit policy TEST_AUDIT_POLICY_HDI enable;
> ```



<a name="loio0bd8fc152db14c798c16b82acf2024ae__section_rnq_sng_4gb"/>

## Auditing Container-Specific SAP HDI Procedures

Developers using SAP HDI typically work within a single container, calling container-specific SAP HDI procedures, for example: writing, reading, and deleting files and folders, or deploying and undeploying these artifacts. The following SQL code shows how to create and enable an audit policy that audits container-specific SAP HDI procedures for a container, named “C”, for example, `C#DI.CANCEL`:

> ### Tip:  
> To apply the following example of an auditing scenario elsewhere, replace “C” with the name of your SAP HDI container.

> ### Sample Code:  
> Auditing SAP HDI Procedures in HDI Container “C”
> 
> ```sql
> create audit policy TEST_AUDIT_POLICY_CONTAINER
>   auditing all 
>   execute on  
>     C#DI.CANCEL,
>     C#DI.CONFIGURE_CONTAINER_PARAMETERS, 
>     C#DI.CONFIGURE_LIBRARIES, 
>     C#DI.DELETE, 
>     C#DI.EXPORT_CONTAINER_FOR_COPY, 
>     C#DI.GET_DEPENDENCIES, 
>     C#DI.GET_MAKE_GROUPS, 
>     C#DI.GRANT_CONTAINER_API_PRIVILEGES, 
>     C#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION,
>     C#DI.GRANT_CONTAINER_SCHEMA_PRIVILEGES, 
>     C#DI.GRANT_CONTAINER_SCHEMA_ROLES, 
>     C#DI.IMPORT_CONTAINER_FOR_COPY, 
>     C#DI.LIST, 
>     C#DI.LIST_CONFIGURED_LIBRARIES, 
>     C#DI.LIST_DEPLOYED, 
>     C#DI.LOCK, 
>     C#DI.MAKE, 
>     C#DI.MAKE_ASYNC, 
>     C#DI.READ, 
>     C#DI.READ_DEPLOYED, 
>     C#DI.REVOKE_CONTAINER_API_PRIVILEGES,
>     C#DI.REVOKE_CONTAINER_SCHEMA_PRIVILEGES, 
>     C#DI.REVOKE_CONTAINER_SCHEMA_ROLES,
>     C#DI.STATUS, 
>     C#DI.WRITE 
>   level info; 
> 
> alter audit policy TEST_AUDIT_POLICY_CONTAINER enable; 
> ```



<a name="loio0bd8fc152db14c798c16b82acf2024ae__section_jrj_x4g_4gb"/>

## Auditing SAP HDI Procedures in All Containers

It is also possible to audit the SAP HDI procedures of **all** containers. Since all container-specific stored procedures call built-in procedures within the “`SYS`” schema, it is sufficient to audit these central built-in procedures if you want to audit the procedure calls of **all** containers. The following example shows how to use SQL to create and enable an audit policy that audits the SAP HDI procedures of **all** HDI containers:

> ### Sample Code:  
> Auditing SAP HDI Procedures in All HDI Containers
> 
> ```sql
> create audit policy TEST_AUDIT_POLICY_ALL_CONTAINERS
> auditing all
> execute on
> SYS.DI_CANCEL_DEV,
> SYS.DI_CONFIGURE_CONTAINER_DEV,
> SYS.DI_CONFIGURE_CONTAINER_PARAMETERS_DEV,
> SYS.DI_CONFIGURE_LIBRARIES_DEV,
> SYS.DI_DELETE_DEV,
> SYS.DI_EXPORT_CONTAINER_FOR_COPY_DEV,
> SYS.DI_GET_DEPENDENCIES_DEV,
> SYS.DI_GET_MAKE_GROUPS_DEV,
> SYS.DI_GRANT_CONTAINER_API_PRIVILEGES_DEV,
> SYS.DI_GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION_DEV,
> SYS.DI_GRANT_CONTAINER_SCHEMA_PRIVILEGES_DEV,
> SYS.DI_GRANT_CONTAINER_SCHEMA_ROLES_DEV,
> SYS.DI_GRANT_DI_SUPPORT_PRIVILEGE_DEV,
> SYS.DI_IMPORT_CONTAINER_FOR_COPY_DEV,
> SYS.DI_LIST_DEV,
> SYS.DI_LIST_CONFIGURED_LIBRARIES_DEV,
> SYS.DI_LIST_DEPLOYED_DEV,
> SYS.DI_LOCK_DEV,
> SYS.DI_MAKE_DEV,
> SYS.DI_MAKE_ASYNC_DEV,
> SYS.DI_READ_DEV,
> SYS.DI_READ_DEPLOYED_DEV,
> SYS.DI_REVOKE_CONTAINER_API_PRIVILEGES_DEV,
> SYS.DI_REVOKE_CONTAINER_SCHEMA_PRIVILEGES_DEV,
> SYS.DI_REVOKE_CONTAINER_SCHEMA_ROLES_DEV,
> SYS.DI_REVOKE_DI_SUPPORT_PRIVILEGE,
> SYS.DI_STATUS_DEV,
> SYS.DI_WRITE_DEV
> level info;
> 
> alter audit policy TEST_AUDIT_POLICY_ALL_CONTAINERS enable;
> ```



<a name="loio0bd8fc152db14c798c16b82acf2024ae__section_xll_lqg_4gb"/>

## Auditing All SAP HDI Database Operations

The standard capabilities provided by the SAP HANA auditing mechanism are sufficient forIn rare cases, it can be helpful to audit all SAP HDI database operations, for example, creating and dropping tables and users, or inserting data into tables. As all those database operations are internally executed by a dedicated SAP HDI transaction owner named “`_SYS_DI_TO`”, it is sufficient to limit auditing to this user. For example, the following SQL command shows how to create and enable an audit policy that audits all SAP HDI database operations for the SAP HDI transaction owner `_SYS_DI_TO`:

> ### Sample Code:  
> Auditing All Database Operations in SAP HDI
> 
> ```sql
> create audit policy TEST_AUDIT_POLICY_ALL_ACTIONS
>   auditing all 
>   actions                
>   for _SYS_DI_TO         
>   level info; 
> 
> alter audit policy TEST_AUDIT_POLICY_ALL_ACTIONS enable;
> ```

**Related Information**  


[SAP HDI Security](sap-hdi-security-d9e5051.md "An overview of the tools used to configure and ensure security in the SAP HANA Deployment Infrastructure (HDI).")

