<!-- loio81fc16bfa4904943b730bcd1848cd37d -->

# ALTER WORKLOAD MAPPING Statement \(Workload Management\)

Changes workload mappings.



## Syntax

```
ALTER WORKLOAD MAPPING <mapping_name> 
   WORKLOAD CLASS <workloadclass_name> [ <property_list> [ <wildcard_option> ] ]
```



## Syntax Elements


<dl>
<dt><b>

*<mapping\_name\>*

</b></dt>
<dd>

Specifies which workload mapping to change.

```
<mapping_name> ::= <identifier>
```



</dd><dt><b>

*<workloadclass\_name\>*

</b></dt>
<dd>

Specifies the workload class name.

```
<workloadclass_name> ::= <identifier>
```



</dd><dt><b>

*<property\_list\>*

</b></dt>
<dd>

Defines the workload mapping properties.

```
<property_list> ::=
 { [ SET <key_value_pair_list> ] | [ UNSET <key_value_pair_list> ] }

<key_value_pair_list> ::= <key_value_pair> [, <key_value_pair> [,…] ]

<key_value_pair> ::= '<key>'='<value>'
```

```
<key> ::= 
 { APPLICATION COMPONENT NAME
 | APPLICATION COMPONENT TYPE 
 | APPLICATION NAME 
 | APPLICATION SOURCE
 | APPLICATION TENANT NAME
 | APPLICATION USER NAME 
 | CLIENT
 | OBJECT NAME
 | SCHEMA NAME 
 | {USER NAME | USERGROUP NAME}
 | XS APPLICATION USER NAME }
```

```
<value> ::= <string_literal>
```

USERGROUP NAME and USER NAME cannot be configured together. For established connections, changes to USERGROUP NAME are only applied when a connected database client reconnects. If there are two matched workload classes by USER NAME and USERGROUP NAME respectively, then USER NAME takes precedence over USERGROUP NAME. APPLICATION TENANT NAME takes lowest precedence.

SCHEMA NAME and OBJECT NAME must be configured together. SCHEMA NAME is the schema of the object. OBJECT NAME can be a procedure name, application function library \(AFL\) area or package name.

If an AFL area or package name is specified, then the workload class is applied to all AFLLANG procedures that call AFs in that AFL area.

If there are multiple workload classes matched by SCHEMA NAME and OBJECT NAME, then the following order of precedence is used applied: AREA --\> PACKAGE --\> PROCEDURE.

XS APPLICATION USER NAME takes precedence over APPLICATION USER NAME.

APPLICATION SOURCE value must be set with setCommandInfo\(\) method for it to be considered when mapping to a workload class.



</dd><dt><b>

*<wildcard\_option\>*

</b></dt>
<dd>

Specifies the wildcard character to use for value matching. All wildcard characters are interpreted as 0 or more characters.

```
<wildcard_option> ::= WITH WILDCARD [ <wildcard-character> ]

 <wildcard-character> ::= <ASCII_character>
```

Wildcard characters can only be ASCII characters and cannot be used with USER NAME or USERGROUP NAME, SCHEMA NAME, or OBJECT NAME.

Only prefix wildcards are supported, for example WILDCARD %.

If no wildcard character is specified, then the default wildcard character is %. Use one wildcard character per property.

If you alter a workload mapping that already has a property with a wildcard and you don't reset the wildcard option, then the property no longer has a wildcard associated with it.



</dd>
</dl>



<a name="loio81fc16bfa4904943b730bcd1848cd37d__section_uzm_wkx_4bb"/>

## Permissions

You need the WORKLOAD ADMIN system privilege.



<a name="loio81fc16bfa4904943b730bcd1848cd37d__section_j5h_ptv_j2b"/>

## Description

Workload mapping settings are stored in the WORKLOAD\_MAPPINGS system view.



## Examples

Change the definition of the MyWorkloadMapping workload mapping to the ABCADM database user and unset the APPLICATION NAME application.

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping" WORKLOAD CLASS "MyWorkloadClass"
   SET 'USER NAME' = 'ABCADM' UNSET 'APPLICATION NAME';
```

The following statement alters the MyWorkloadMapping1 workload mapping to use the wildcard character % by default for value matching:

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'APPLICATION NAME' = 'BW%' WITH WILDCARD;
```

The following statement alters the MyWorkloadMapping1 workload mapping to update the application name to be BW%\* \(without a wildcard\):

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'APPLICATION NAME' = 'BW%*';
```

The following statement alters the MyWorkloadMapping1 workload mapping to set the user group name to USERGROUP\_TEST.

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'USERGROUP NAME' = 'USERGROUP_TEST';
```

The following statement alters an entry for the "BW\_SYSTEM" workload mapping for the object SYS.CHECK\_ES.

```
ALTER WORKLOAD MAPPING "BW_SYSTEM" WORKLOAD CLASS "DATAMART" SET 'SCHEMA NAME' = 'SYS', 'OBJECT NAME' = 'CHECK_ES';
```

The following statement alters an entry for the MyWorkloadMapping1 workload mapping for the XS application user name TESTER.

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "DATAMART" SET 'XS APPLICATION USER NAME' = 'TESTER';
```

The following statement alters an entry for the MyWorkloadMapping1 workload mapping where APPLICATION SOURCE exactly matches example.cc:456.

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyClass1" SET 'APPLICATION SOURCE' = 'example.cc:456';
```

The following statement alters the MyWorkloadMapping1 workload mapping to exclude APPLICATION SOURCE.

```
ALTER WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyClass1" UNSET 'APPLICATION SOURCE';
```

**Related Information**  


[WORKLOAD\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/workload-mappings-system-view-89a0660.md "Provides information about available workload mappings.")

[CREATE WORKLOAD MAPPING Statement \(Workload Management\)](create-workload-mapping-statement-workload-management-996978a.md "Defines workload mappings.")

