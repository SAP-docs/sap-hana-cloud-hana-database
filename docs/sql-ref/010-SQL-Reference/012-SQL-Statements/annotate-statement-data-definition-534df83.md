<!-- loio534df83ee61946b884e7594d21459e35 -->

# ANNOTATE Statement \(Data Definition\)

Annotates SQL objects such as tables, views, columns, table functions, procedures, and parameters.



<a name="loio534df83ee61946b884e7594d21459e35__section_kbn_5gz_kbb"/>

## Syntax

```
ANNOTATE { [ <table_annotations> ] | [ <column_annotations> ] | [ <parameter_annotations> ] } )

<table_annotations> ::= { [ <key_set_operation> ] [ <key_unset_operation> ] }

<column_annotations> ::= <column_annotation> [ <column_annotation> […] ]
<column_annotation> ::= COLUMN <column_ref> { <key_set_operation> | <key_unset_operation> }


<parameter_annotations> ::= <parameter_annotation> [ <parameter_annotation> […] ]
<parameter_annotation> ::= PARAMETER <column_ref> { <key_set_operation> | <key_unset_operation> }

<key_set_operation> ::= SET <key_value_pair_list> 
<key_unset_operation> ::= UNSET <key_list>

<key_value_pair_list> ::= <key_value_pair> [, <key_value_pair> [,…] ]
<key_value_pair> ::= '<key>'='<value>'
<key_list> ::= { '<key>'[,'<key>'[,…] ] | ALL }
```



<a name="loio534df83ee61946b884e7594d21459e35__section_lbn_5gz_kbb"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_ref\>*

</b></dt>
<dd>

Specifies a table, view, table function, or procedure.

```
<table_ref> ::= [ <schema>.]{ <table_name> | <view_name> }
```



</dd><dt><b>

COLUMN *<column\_ref\>*

</b></dt>
<dd>

Specifies a column of a table or view.

```
<column_ref> ::= COLUMN [ <schema>.]{ <table_name> | <view_name> }.<column_name>
```



</dd><dt><b>

PARAMETER *<parameter\_ref\>*

</b></dt>
<dd>

Specifies a parameter of a procedure or function.

```
<parameter_ref> ::= PARAMETER [ <schema>.]{ <procedure_name> | <function_name> }.<parameter_name>
```



</dd><dt><b>

*<annotation\_operation\>*

</b></dt>
<dd>

Specifies the annotation to perform.

```
<annotation_operation> ::=  
 SET <key> = <value> 
 | UNSET { <key> | ALL } 
```

Use SET to annotate the specified database object with a key/value pair. If the key already exists for the database object, then the existing value is replace by *<value\>*.

Use UNSET to remove the key/value pair identified by *<key\>* for the specified database object, or use UNSET ALL to remove all key/value pair annotations for the specified database object.

*<key\>* and *<value\>* are string literals that specify the annotation as a key/value pair \(for example, 'key1'='20'\) .



</dd>
</dl>



<a name="loio534df83ee61946b884e7594d21459e35__section_mbn_5gz_kbb"/>

## Description

SQL Annotation, a form of metadata, provides additional insight into an SQL object.

Annotated values for database objects are stored in the ANNOTATIONS system view.



<a name="loio534df83ee61946b884e7594d21459e35__section_ybv_4sg_2cb"/>

## Permissions

You must have ALTER object privilege on the object to annotate it.



<a name="loio534df83ee61946b884e7594d21459e35__section_ylj_gcd_dcb"/>

## Examples

The following statements create a function and annotate it:

```
CREATE FUNCTION add_shipping_func(price DECIMAL(15,2), shipping DECIMAL(15,2))
RETURNS result DECIMAL(15,2)
LANGUAGE SQLSCRIPT  
SQL SECURITY INVOKER AS
BEGIN
result := :price + :shipping;
END;

ANNOTATE add_shipping_func SET 'region'='EMEA';
ANNOTATE PARAMETER add_shipping_func.price SET 'currency'='USD';
ANNOTATE PARAMETER add_shipping_func.shipping SET 'currency'='USD';
```

The following statements replaces the value for the `currency` annotations on the `price` parameter:

```
ANNOTATE PARAMETER add_shipping_func.price SET 'currency'='CAD';
```

The following statement removes the `currency` annotation on the `shipping` parameter:

```
ANNOTATE PARAMETER add_shipping_func.shipping UNSET 'currency';
```

The following statement creates a table, adds some annotations, and then removes them all.

```
CREATE COLUMN TABLE t1 ( col1 INT NOT NULL);
ANNOTATE t1 SET 'priority'='high';
ANNOTATE COLUMN t1.col1 SET 'datatype'='integer';
ANNOTATE COLUMN t1.col1 SET 'nullability'='no nulls';
ANNOTATE COLUMN t1.col1 UNSET ALL;
ANNOTATE t1 UNSET 'priority';
```

**Related Information**  


[ANNOTATIONS System View](../../020-System-Views-Reference/021-System-Views/annotations-system-view-da2b930.md "Provides information about annotations that have been added to SQL objects.")

