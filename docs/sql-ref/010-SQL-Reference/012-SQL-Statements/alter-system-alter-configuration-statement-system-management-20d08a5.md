<!-- loio20d08a5b751910148145dbc016c826a4 -->

# ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)

Sets or removes configuration parameters in an INI file.



<a name="loio20d08a5b751910148145dbc016c826a4__sql_alter_system_alter_configuration_1sql_alter_system_alter_configuration_syntax"/>

## Syntax

```
ALTER SYSTEM ALTER CONFIGURATION ( <filename>, <layer>[, <layer_name> ] )
 { SET | UNSET } <parameter_key_value_list> 
 [ WITH RECONFIGURE ]
 [ COMMENT <comment_string> ]
```



<a name="loio20d08a5b751910148145dbc016c826a4__sql_alter_system_alter_configuration_1sql_alter_system_alter_configuration_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<filename\>*

</b></dt>
<dd>

The filename of the configuration file to be modified. If the file does not exist on the required layer, the file is created when a SET command is used.

```
<filename> ::= <string_literal>
```



</dd><dt><b>

*<layer\>*

</b></dt>
<dd>

Sets the target layer for the configuration change. Specify DATABASE for settings relevent for the database. Specify HOST for minor configurations for a host and specify the target host name using *<layer\_name\>*.

```
<layer> ::= <'HOST' | 'DATABASE'>
```



</dd><dt><b>

*<layer\_name\>*

</b></dt>
<dd>

If the layer parameter above is set to 'HOST', *<layer\_name\>* is used to target either a tenant name or a target host name. For example, 'selxeon12' would target the 'selxeon12' host.

```
 <layer_name> ::= <string_literal>
```

> ### Note:  
> The 'HOST' value must be provided in lowercase only.



</dd><dt><b>

SET

</b></dt>
<dd>

Updates the value of a key if the key already exists, or inserts a new key if required.



</dd><dt><b>

UNSET

</b></dt>
<dd>

Removes a key and its associated value.



</dd><dt><b>

*<parameter\_key\_value\_list\>*

</b></dt>
<dd>

A list of configuration file entries to be modified or removed.

```
<parameter_key_value_list> ::= <parameter_key_value_entry> 
   [{, <parameter_key_value_entry>}...]
```


<dl>
<dt><b>

*<parameter\_key\_value\_entry\>*

</b></dt>
<dd>

Specifies the section, key and value of the `.ini` file parameter to be created, modified, or removed.

```
<parameter_key_value_entry> ::= (<section_name>,<parameter_name>)
   [ = <parameter_value>]
```



</dd><dt><b>

*<section\_name\>*

</b></dt>
<dd>

Specifies the section name of the parameter to be modified

```
<section_name> ::= <string_literal>
```



</dd><dt><b>

*<parameter\_name\>*

</b></dt>
<dd>

Specifies the name of the parameter to be modified.

```
<parameter_name> ::= <string_literal>
```



</dd><dt><b>

*<parameter\_value\>*

</b></dt>
<dd>

Specifies the value of the parameter.

```
<parameter_value> ::= <string_literal>
```



</dd>
</dl>



</dd><dt><b>

WITH RECONFIGURE

</b></dt>
<dd>

Specifies that the configuration changes are directly applied to the running database instance.

When WITH RECONFIGURE is not specified the configuration changes are written to the required `.ini` file, however the modified values are not applied to the current running system. The changes are only applied during a restart of the database or a subsequent configuration change with WITH RECONFIGURE. In this case there can be inconsistencies between the `.ini` file contents and the actual configuration value that the SAP HANA database is currently using.



</dd><dt><b>

COMMENT *<comment\_string\>*

</b></dt>
<dd>

Specifies a free-text comment \(string literal\) that could be used to explain why an `.ini` file parameter is being changed.



</dd>
</dl>



<a name="loio20d08a5b751910148145dbc016c826a4__sql_alter_system_alter_configuration_1sql_alter_system_alter_configuration_description"/>

## Description

Sets or removes configuration parameters in an INI file.

By default, an error is returned if a settings is set to an unsupported value.

For a list of configuration parameters, see the *SAP HANA Cloud, SAP HANA Database Configuration Parameter Reference*.



<a name="loio20d08a5b751910148145dbc016c826a4__section_wth_ytq_xrb"/>

## Permissions

You must have the INIFILE ADMIN system privilege to modify configuration parameters in an INI file.



<a name="loio20d08a5b751910148145dbc016c826a4__sql_alter_system_alter_configuration_1sql_alter_system_alter_configuration_examples"/>

## Example

Set a parameter new\_test\_value in the alt\_sys\_test section of the `global.ini` file.

```
ALTER SYSTEM ALTER CONFIGURATION ('global.ini', 'DATABASE') 
   SET ('alt_sys_test', 'new_test_value') = 'test';
```

**Related Information**  


[SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/2024_3_QRC/en-US/4b4d88980622427ab2d6ca8c05448166.html "Reference documentation for public configuration parameters in SAP HANA Cloud.") :arrow_upper_right:

[Configuring SAP HANA System Properties (INI Files)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/3f1a6a7dc31049409e1a9f9108d73d51.html "An SAP HANA database has several configuration (*.ini) files that contain properties for configuring the database and services.") :arrow_upper_right:

[M\_INIFILES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifiles-system-view-20b18dc.md "Provides information about all configuration files.")

[M\_INIFILE\_CONTENT\_HISTORY System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifile-content-history-system-view-a42a0b8.md "Provides change history information for configuration (ini) files.")

[M\_INIFILE\_CONTENTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifile-contents-system-view-20b16a7.md "Provides configuration information from INI files.")

