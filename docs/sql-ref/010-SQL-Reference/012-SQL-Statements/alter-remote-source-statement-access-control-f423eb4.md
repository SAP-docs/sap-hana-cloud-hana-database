<!-- loiof423eb496f5b1014a1a7bb3e49bcc07b -->

# ALTER REMOTE SOURCE Statement \(Access Control\)

Modifies the configuration of an external data source that is connected to an SAP HANA database.





<a name="loiof423eb496f5b1014a1a7bb3e49bcc07b__sql_alter_remote_source_1sql_alter_remote_source_syntax"/>

## Syntax

```
ALTER REMOTE SOURCE <remote_source_name> [ <adapter_clause> ] [ <credential_clause> ]
 | ALTER REMOTE SOURCE <remote_source_name> { <refresh_clause> | <drop_clause> }
 | ALTER REMOTE SOURCE <remote_source_name> [ <properties_clause> ]
```



<a name="loiof423eb496f5b1014a1a7bb3e49bcc07b__sql_alter_remote_source_1sql_alter_remote_source_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<remote\_source\_name\>*

</b></dt>
<dd>

Specifies the identifier of the remote source.

```
<remote_source_name> ::= <identifier>
```



</dd>
</dl>


<dl>
<dt><b>

*<adapter\_clause\>*

</b></dt>
<dd>

Specifies the adapter configuration.

```
<adapter_clause> ::= 
 [ ADAPTER <adapter_name> [ CONFIGURATION FILE <configuration_file> ] CONFIGURATION <connection_info_string> ]
```


<dl>
<dt><b>

*<adapter\_name\>*

</b></dt>
<dd>

Specifies the adapter to be used to access the remote data. Query the ADAPTERS system view for the list of available adapter names.

```
<adapter_name> ::= <identifier>
```



</dd><dt><b>

*<configuration\_file\>*

</b></dt>
<dd>

Specifies the configuration file for the specified adapter.



</dd>
</dl>


<dl>
<dt><b>

*<connection\_info\_string\>*

</b></dt>
<dd>

Specifies the connection parameters for a given adapter.

For an on-premise remote source:

```
<connection_info_string> ::= 
   { 'DSN=<DSN_entry_name>' 
     | ' { webhdfs.url=http://<host_name>:50070/;webhcat.url=http://<host_name>:50111 
         | Driver=<ODBC_library>; ServerNode=<machine_name>:3<instance#>15 }
       [,<failover_server_name>:3<failover_instance_number>15 ]
       [ ;sessionVariable:<session_variable_name>=? ]
       [ ;linkeddatabase_mode=optimized ] } ' 
   }
```

For an SAP HANA service instance remote source:

```
<connection_info_string> ::= 
   { 'DSN=<DSN_entry_name>'
     | ' { webhdfs.url=http://<host_name>:50070/;webhcat.url=http://<host_name>:50111 
         | Driver=<ODBC_library>; ServerNode=<tenant_endpoint> }
       [,<failover_tenant_endpoint> ]
       [ ;sslTrustStore="<certificate_string>";encrypt=TRUE; ]
       [ ;sessionVariable:<session_variable_name>=? ]
       [ ;linkeddatabase_mode=optimized ] } '
   } 
```

The failover, session variable, and linked database parameters are only supported for SAP HANA remote sources.



</dd>
</dl>



</dd>
</dl>


<dl>
<dt><b>

*<credential\_clause\>*

</b></dt>
<dd>

Specifies the credential configuration.

```
<credential_clause> ::= WITH CREDENTIAL TYPE <credential_type> | DROP CREDENTIAL TYPE [ 'KERBEROS' | 'PASSWORD' ]
```


<dl>
<dt><b>

*<credential\_type\>*

</b></dt>
<dd>

Specifies a credential type and the credential.

```
<credential_type> ::= { 'KERBEROS' | 'PASSWORD' [ USING <credentials> ] }
```



</dd>
</dl>



</dd>
</dl>


<dl>
<dt><b>

*<drop\_clause\>*

</b></dt>
<dd>

Delete all linked objects associated with a linked database using the remote source.

```
<drop_clause> ::= DROP LINKED OBJECTS [ CASCADE | RESTRICT ]

```

The CASCADE option drops all the linked tables and dependent objects associated with linked tables. The RESTRICT option drops linked tables are dropped only if there are no dependencies on any of the linked tables. If this option is used and there are dependent objects on a linked table, then an error is raised, and all linked tables are retained. If no drop option is specified, then all internally generated linked tables with no dependencies are dropped. Linked tables with dependencies are retained.



</dd>
</dl>


<dl>
<dt><b>

*<refresh\_option\>*

</b></dt>
<dd>

Refreshes metadata for a single linked table or all linked objects using the remote source.

```
<refresh_option> ::= REFRESH LINKED { OBJECTS | TABLE <table_name> }

<table_name> ::= <remote_source_name>.<schema_name>.<identifier>
```

*<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd>
</dl>


<dl>
<dt><b>

*<properties\_clause\>*

</b></dt>
<dd>

Changes the value of one or more properties of a single remote source.

```
<properties_clause> ::= { SET PROPERTY <prop_definition_list> | UNSET PROPERTY { ALL | <prop_list> } }

<prop_definition_list> ::= <prop_definition> [, <prop_definition> [ ,... ] ]
<prop_definition> ::= <prop_name> = <prop_value> [ <prop_name> = <prop_value> [,... ] ]
<prop_list> ::= <prop_name> [ , <prop_name> [ ,... ] ]
```

SET replaces the default property value with a new value. UNSET returns the property value to its default value. For a list of properties that can be set for a remote source, see *Listing Remote Source Properties* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



</dd>
</dl>



<a name="loiof423eb496f5b1014a1a7bb3e49bcc07b__sql_alter_remote_source_1sql_alter_remote_source_description"/>

## Description

For more information on creating remote sources, see the *SAP HANA Cloud, SAP HANA Database Administration Guide* .



<a name="loiof423eb496f5b1014a1a7bb3e49bcc07b__section_opr_ddt_5cb"/>

## Permissions

You must have the ALTER object privilege on the remote source.



<a name="loiof423eb496f5b1014a1a7bb3e49bcc07b__sql_alter_remote_source_1sql_alter_remote_source_examples"/>

## Example

This example alters the remote source MY\_REMOTE1 to use the HANA adapter, DSN entry MYHANA1, and set a new technical user credential for the source.

```
ALTER REMOTE SOURCE MY_REMOTE1 ADAPTER HANAODBC CONFIGURATION 'DSN=MYHANA1' 
   WITH CREDENTIAL TYPE 'PASSWORD' USING 'user="user1";password="Password1"';
```

This example drops the technical user credential for the MY\_REMOTE1 remote source.

```
ALTER REMOTE SOURCE MY_REMOTE1 DROP CREDENTIAL TYPE 'PASSWORD';
```

This example clears all internally generated objects associated with remote source MY\_REMOTE1 and drops any dependent objects that reference the linked object.

```
ALTER REMOTE SOURCE MY_REMOTE1 DROP LINKED OBJECTS CASCADE;
```

This example refreshes the metadata of all linked objects associated with remote source MY\_REMOT1E.

```
ALTER REMOTE SOURCE MY_REMOTE1 REFRESH LINKED OBJECTS;
```

This example refreshes the metadata for remote table MYSCHEMA.MYTABLE on remote source MY\_REMOTE1.

```
ALTER REMOTE SOURCE MY_REMOTE REFRESH LINKED TABLE MY_REMOTE1.MYSCHEMA.MYTABLE;
```

This example enables failover, sets the session variable APPLICATIONUSER, and enables optimized mode for linked database on the SAP HANA remote source MY\_REMOTE1.

```
ALTER REMOTE SOURCE MY_REMOTE1 ADAPTER HANAODBC
     CONFIGURATION 'Driver=libodbcHDB.so;ServerNode=my_machine1:30115,failover_machine1:30215
     sessionVariable:APPLICATIONUSER=?;linkeddatabase_mode=optimized]’;
```

This example sets two properties on the remote source RS1

```
ALTER REMOTE SOURCE RS1 SET PROPERTY 'CAP_LIMIT' = 'true', 'PROP_USE_UNIX_MANAGER'= 'true';
```

This example unsets all properties on remote source RS1

```
ALTER REMOTE SOURCE RS1 UNSET PROPERTY ALL;
```

**Related Information**  


[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Configure Remote Source Capabilities](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/59e0ffd04ce04eb792331315c9e984fb.html "Customize the behavior of capabilities for your remote source.") :arrow_upper_right:

