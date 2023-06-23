<!-- loio20d364c175191014b592f500ccb5510c -->

# CALL Statement \(Procedural\)

Calls a procedure.



<a name="loio20d364c175191014b592f500ccb5510c__sql_call_1sql_call_syntax"/>

## Syntax

```
CALL <proc_name> ( <param_list> ) [ <hint_clause> ]
 | CALL <sqlscript_lib_member> ( <param_list> )
```



<a name="loio20d364c175191014b592f500ccb5510c__sql_call_1sql_call_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<proc\_name\>*

</b></dt>
<dd>

Specifies the procedure to be called.

```
<proc_name> ::= [ <schema_name>.]<identifier>
```

Optionally, specify a schema name for the identifier.



</dd><dt><b>

*<param\_list\>*

</b></dt>
<dd>

Specifies the procedure parameters.

```
<param_list> ::= <proc_param>[,...]
```


<dl>
<dt><b>

*<proc\_param\>*

</b></dt>
<dd>

Specifies procedure parameters.

```
<proc_param> ::=
 <identifier>
 | <string_literal>
 | <unsigned_integer>
 | <signed_integer>
 | <signed_numeric_literal>
 | <unsigned_numeric_literal>
 | <expressions>
```

Parameters passed to a procedure are scalar constants and can be passed either as IN, OUT, or INOUT parameters. Scalar parameters are assumed to be NOT NULL. Arguments for IN parameters of table type can either be physical tables or views. The actual value passed for tabular OUT parameters must be ?.



</dd>
</dl>



</dd><dt><b>

*<hint\_clause\>*

</b></dt>
<dd>

Specifies a hint to use for the CALL.

```
<hint_clause> ::= WITH HINT ( <hint> [, <hint> ...] )

<hint> ::= { <hint_element> | <routing_hint> | <value_input> } [ CASCADE ]

<hint_element> ::= <hint_name> from public hint list [(<hint_argument_list>)]<hint_argument_list>

<hint_argument_list> ::= <hint_argument> [, <hint_argument> ...]

<hint_argument> ::= hint argument type according to each hint specification (for example, one of STR_CONST, INT_CONST,  ID, or <table_ref>)

<routing_hint> ::=
   ROUTE_TO( <volumd_id> [, <volumd_id> [,...] ] )
   | ROUTE_TO( <service_type> [, <service_type> [,...] ] )
   | NO_ROUTE_TO( <volumd_id> [, <volumd_id> [,...] ] )
   | NO_ROUTE_TO( <service_type> [, <service_type> [,...] ] )
   | ROUTE_BY( { <table_name> | <projection_view_name> } [ ,{ <table_name> | <projection_view_name> } [,...] ] )
   | ROUTE_BY_CARDINALITY( { <table_name> | <projection_view_name> } [, { <table_name> | <projection_view_name> } [,...] ] )

<value_input> ::= MAX_CONCURRENCY (1) | DATA_TRANSFER_COST ({0 | 1})
```

For a list of available hints by category, see [HINT Details](hint-details-4ba9edc.md).


<dl>
<dt><b>

CASCADE

</b></dt>
<dd>

Allows propagation of a hint into internal SQL statements within a procedure. The HINT is applied to both the CALL statement itself and any internal SQLs. If CASCADE is used for non-CALL statements, a FEATURE NOT SUPPORTED message appears. CASCADE is only supported in CALL statements and cannot propagate hints into user-defined functions. When there are nested CALL statements, CASCADE hints are also propagated into the nested procedures.



</dd>
</dl>



</dd><dt><b>

*<sqlscript\_lib\_member\>*

</b></dt>
<dd>

Calls a SQLScript library member procedure.

```
<lib_member_ref> ::= [ <schema_name>.]<library_name_or_alias>:<member_name>
 
<schema_name> ::= <identifier>
<library_name_or_alias> ::= <identifier>
<member_name> ::= <identifier>

```

When calling a SQLScript library member procedure, the WITH option is not supported. Also, there is no EXPLAIN PLAN or QUERY EXPORT support when calling a SQLScript library member procedure.

For more information about SQLScript user-defined libraries, see the *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



</dd>
</dl>



<a name="loio20d364c175191014b592f500ccb5510c__sql_call_1sql_call_description"/>

## Description

Calls a procedure defined using the CREATE PROCEDURE statement.

CALL conceptually returns list of result sets with one entry for every tabular result. An iterator can be used to iterate over these results sets. For each result set you can iterate over the result table in the same way as for query results. SQL statements that are not assigned to any table variable in the procedure body are added as result sets at the end of the list of result sets. The type of the result structures is determined during compilation time, but it is not visible in the signature of the procedure.

When executed by the client, the CALL syntax behaves in a way consistent with the SQL standard semantics; for example, Java clients can call a procedure using a JDBC CallableStatement. Scalar output variables are a scalar value that can be retrieved from the callable statement directly.

Unquoted identifiers are implicitly treated as upper case. Quoting identifiers respect capitalization and allow for using white spaces which are normally not allowed in SQL identifiers.



<a name="loio20d364c175191014b592f500ccb5510c__sql_call_1sql_call_examples"/>

## Examples

Call the getOutput procedure in debug mode.

```
CALL getOutput (1000, 'EUR', NULL, NULL) IN DEBUG MODE;
```

The following example creates a library with one member procedure and then calls the member procedure directly using the CALL statement:

```
CREATE LIBRARY MyLib AS BEGIN
  PUBLIC PROCEDURE MemberProc(IN i INT, OUT tv TABLE(Col1 NVARCHAR(10))) AS BEGIN
    tv = SELECT :i * 100 AS Col1 FROM DUMMY;
  END;
END;
 
CALL MyLib:MemberProc(1, ?);
```

**Related Information**  


[Table Variable Type Definition](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/ea5065d06d14426799d879234d8e3e7b.html "") :arrow_upper_right:

[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[SQL Notation Conventions](../sql-notation-conventions-209e0cd.md "SQL syntax notation conventions used in this guide.")

[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

