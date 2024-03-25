<!-- loio55d2f440e375408194be7e58266733fa -->

# CREATE VIRTUAL FUNCTION Statement \(Procedural\)

Creates a virtual table user-defined function \(TUDF\) that points to a remote table user-defined function in another SAP HANA Cloud, SAP HANA database or in an SAP HANA on-premise system.



## Syntax

```
CREATE VIRTUAL FUNCTION <virtual_function_name> AT <remote_location_clause>
```



## Syntax Elements


<dl>
<dt><b>

*<virtual\_function\_name\>*

</b></dt>
<dd>

Specifies the virtual function name, with optional schema name.

```
<virtual_function_name> ::= [<schema_name>.]<identifier>
```



</dd>
</dl>


<dl>
<dt><b>

*<remote\_location\_clause\>*

</b></dt>
<dd>

Specifies the location of the remote table user-defined function.



</dd>
<dd>

```
<remote_location_clause> ::=
"<remote_source>"."<database_name>"."<remote_schema_name>"."<remote_function_name>"
```



</dd>
</dl>



## Description

A virtual table user-defined function lets you pass parameters to the corresponding remote table user-defined function to retrieve data from the remote database, which is returned as a table. Virtual table user-defined functions are read-only and can only be used with SELECT statements. They cannot be used with other data manipulation statements such as INSERT, DELETE, UPDATE, REPLACE, or MERGE INTO.



<a name="loio55d2f440e375408194be7e58266733fa__section_opr_ddt_5cb"/>

## Permissions

This statement requires the CREATE VIRTUAL FUNCTION object privilege on the remote source.



## Example

The following example creates a virtual function VTUDF1 that points to remote table user-defined function TUDF1.

```
CREATE VIRTUAL FUNCTION MYSCHEMA1.VTUDF1 AT "HANA1"."DB1"."MYSCHEMA2"."TUDF1";
```

**Related Information**  


[Create a Virtual Table User-Defined Function \(SAP HANA Cloud, SAP HANA Database Data Access Guide\)](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-data-access-guide/create-virtual-table-user-defined-function)

[System Views for Monitoring Virtual Table User-Defined Functions \(SAP HANA Cloud, SAP HANA Database Data Access Guide\)](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-data-access-guide/system-views-for-monitoring-virtual-table-user-defined-functions)

