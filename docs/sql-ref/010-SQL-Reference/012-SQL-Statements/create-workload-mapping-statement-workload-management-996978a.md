<!-- loio996978a669b847ea89ca7f2cce41d916 -->

# CREATE WORKLOAD MAPPING Statement \(Workload Management\)

Defines workload mappings.



## Syntax

```
CREATE WORKLOAD MAPPING <mapping_name> 
   WORKLOAD CLASS <workloadclass_name> [ <property_list> [ <wildcard_option> ] ]
```



## Syntax Elements


<dl>
<dt><b>

*<mapping\_name\>*

</b></dt>
<dd>

Specifies the name for the new workload mapping.

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

Specifies the wildcard character to use for value matching.

```
<wildcard_option> ::= WITH WILDCARD [ <wildcard-character> ]

<wildcard-character> ::= <ASCII_character>
```

Wildcard characters can only be ASCII characters and cannot be used with USER NAME or USERGROUP NAME, SCHEMA NAME, or OBJECT NAME.

Only prefix wildcards are supported, for example WILDCARD %.

If no wildcard character is specified, then the default wildcard character is %. Use one wildcard character per property.



</dd>
</dl>



<a name="loio996978a669b847ea89ca7f2cce41d916__section_fvl_skx_4bb"/>

## Permissions

You need the WORKLOAD ADMIN system privilege.



## Description

This statement defines workload mappings.

Workload mapping settings are stored in the WORKLOAD\_MAPPINGS system view.



## Examples

The following statement creates an entry for the MyWorkloadMapping1 workload mapping for the ABCADM database user and the BW application.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'USER NAME' = 'ABCADM', 'APPLICATION NAME' = 'BW';
```

The following statement uses the wildcard character % by default for value matching any application name that begins with BW.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'APPLICATION NAME' = 'BW%' WITH WILDCARD;
```

The following two statements both result in an error since the wildcard must be placed at the end of the property value.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'APPLICATION NAME' = 'BW%123' WITH WILDCARD;
```

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'APPLICATION NAME' = 'BW%*123' WITH WILDCARD '*';
```

The following statement creates an entry for the MyWorkloadMapping1 workload mapping for the USERGROUP\_TEST user group.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyWorkloadClass" SET 'USERGROUP NAME' = 'USERGROUP_TEST';
```

The following statement creates an entry for the "MyWorkloadMapping1" workload mapping for the object SYS.CHECK\_ES.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "DATAMART" SET 'SCHEMA NAME' = 'SYS', 'OBJECT NAME' = 'CHECK_ES';
```

The following statement creates an entry for the MyWorkloadMapping1 workload mapping for the XS application user name TESTER.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "DATAMART" SET 'XS APPLICATION USER NAME' = 'TESTER';
```

The following statement uses the wildcard character % by default for any creates XS application user name that begins with ADMIN.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "DATAMART" SET 'XS APPLICATION USER NAME' = 'ADMIN%' WITH WILDCARD;
```

The following statements create workload mappings for APPLICATION TENANT NAME:

```
CREATE WORKLOAD MAPPING "DWC_MAP1" WORKLOAD CLASS "DWC_CLS1" SET 'APPLICATION TENANT NAME' ='DWC_SPACE1';
CREATE WORKLOAD MAPPING "DWC_MAP2" WORKLOAD CLASS "DWC_CLS2" SET 'APPLICATION TENANT NAME' ='DWC_SPACE2%' WITH WILDCARD;

```

The following statement creates an entry for the MyWorkloadMapping1 workload mapping where the APPLICATION SOURCE value is exactly “example.cc:123”.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyClass1" SET 'APPLICATION SOURCE' = 'example.cc:123';
```

The following statement uses the wildcard character % for any APPLICATION SOURCE value that begins with “example.cc:”.

```
CREATE WORKLOAD MAPPING "MyWorkloadMapping1" WORKLOAD CLASS "MyClass1" SET 'APPLICATION SOURCE' = 'example.cc:%' WITH WILDCARD '%';
```

**Related Information**  


[WORKLOAD\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/workload-mappings-system-view-89a0660.md "Provides information about available workload mappings.")

[ALTER WORKLOAD MAPPING Statement \(Workload Management\)](alter-workload-mapping-statement-workload-management-81fc16b.md "Changes workload mappings.")

[Managing Workload with Workload Classes](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/5066181717df4110931271d1efd84cbc.html "You can manage workload in SAP HANA by creating workload classes and workload class mappings. Appropriate workload parameters are then dynamically applied to each client session.") :arrow_upper_right:

[Session Variables](../session-variables-a16678c.md " 		 		 		 		 		 		 	")

