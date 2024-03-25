<!-- loio20d48343751910149985a2c925e12190 -->

# CREATE REMOTE SOURCE Statement \(Access Control\)

Defines an external data source that can connect to the SAP HANA database.



<a name="loio20d48343751910149985a2c925e12190__sql_create_remote_source_1sql_create_remote_source_syntax"/>

## Syntax

```
CREATE REMOTE SOURCE <remote_source_name> <adapter_clause> [ <credential_clause> ]
```



<a name="loio20d48343751910149985a2c925e12190__sql_create_remote_source_1sql_create_remote_source"/>

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



</dd><dt><b>

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

Specifies the corresponding adapter, and the type of access method, to be used by the SAP HANA database to access the data. Query the ADAPTERS system view for the list of adapter names you can specify.\`

```
<adapter_name> ::= <identifier>
```



</dd><dt><b>

*<configuration\_file\>*

</b></dt>
<dd>

Specifies the configuration file for the specified adapter.



</dd><dt><b>

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



</dd><dt><b>

*<credential\_clause\>*

</b></dt>
<dd>

Specifies the credential configuration.

```
<credential_clause> ::= WITH CREDENTIAL TYPE <credential_type> [ USING <credentials> ]
```


<dl>
<dt><b>

*<credential\_type\>*

</b></dt>
<dd>

Supported credential types:

```
<credential_type> ::= { 'KERBEROS' | 'PASSWORD' | 'JWT' | 'X509' PSE <PSE_name> }
```

-   PASSWORD: requires a cleartext user name and password to be used as credential information

-   KERBEROS: uses the existing Kerberos configuration

-   JWT: uses JSON Web Token \(JWT\) single sign-on \(SSO\) for smart data access \(SDA\)

-   X509: uses the X509 credential type with the specified PSE name.




</dd><dt><b>

USING *<credentials\>*

</b></dt>
<dd>

Specifies the user name and password for *<credential\_type\>* PASSWORD.

```
<credentials> ::= 'user=<user_name>;password=<password>'
```



</dd>
</dl>



</dd>
</dl>



<a name="loio20d48343751910149985a2c925e12190__section_opr_ddt_5cb"/>

## Permissions

This statement requires the CREATE REMOTE SOURCE system privilege. To use the x509 credential type also requires the REFERENCES object-level privilege on the PSE.



<a name="loio20d48343751910149985a2c925e12190__sql_create_remote_source_1sql_create_remote_source_description"/>

## Description

For more information on creating remote sources, see *Creating a Remote Source* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



<a name="loio20d48343751910149985a2c925e12190__sql_create_remote_source_1sql_create_remote_source_examples"/>

## Example

This example creates a remote source named HOSTB on the HANA adapter. Details for the remote ODBC configuration are passed via the `libodbcHDB.so` driver. Kerberos is used for authentication.

```
CREATE REMOTE SOURCE HOSTB ADAPTER hanaodbc
    CONFIGURATION 'Driver=libodbcHDB.so;ServerNode=my_hanaserver:30115;' 
    WITH CREDENTIAL TYPE 'KERBEROS';
```

This example create a HANA remote source name HOSTC. Failover on the remote source is enabled. The session variable APPLICATIONUSER is set and optimized mode is enabled for linked database.

```
CREATE REMOTE SOURCE HOSTC ADAPTER hanaodbc
    CONFIGURATION 'Driver=libodbcHDB.so;ServerNode=my_hanaserver:30115,my_failover_hanaserver:30215;
    sessionVariable:APPLICATIONUSER=?;linkeddatabase_mode=optimized]'
    WITH CREDENTIAL TYPE 'PASSWORD' USING 'user=dbuser;password=DBtest123';
```

**Related Information**  


[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[ALTER REMOTE SOURCE Statement \(Access Control\)](alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[ADAPTERS System View](../../020-System-Views-Reference/021-System-Views/adapters-system-view-6d91840.md "Displays adapters available in the SAP HANA system.")

[CREATE PSE Statement \(System Management\)](create-pse-statement-system-management-4d80bf6.md "Creates a personal security environment (PSE).")

