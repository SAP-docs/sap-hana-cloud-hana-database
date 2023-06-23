<!-- loio20d7a85b751910149482f673a4789209 -->

# DROP SEQUENCE Statement \(Data Definition\)

Removes a sequence.



<a name="loio20d7a85b751910149482f673a4789209__sql_drop_sequence_1sql_drop_sequence_syntax"/>

## Syntax

```
DROP SEQUENCE <sequence_name> [<drop_option>]
```



<a name="loio20d7a85b751910149482f673a4789209__sql_drop_sequence_1sql_drop_sequence_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<sequence\_name\>*

</b></dt>
<dd>

Drops the specified sequence, with the optional schema name.

```
<sequence_name> ::= [<schema_name>.]<identifier>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= CASCADE | RESTRICT
```

CASCADE drops the sequence and dependent objects. RESTRICT drops the sequence only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.

If *<drop\_option\>* is not specified, then a non-cascaded drop is performed, which only drops the specified sequence. Dependent objects of the sequence are invalidated but not dropped.



</dd>
</dl>



<a name="loio20d7a85b751910149482f673a4789209__sql_drop_sequence_1sql_drop_sequence_description"/>

## Description

The DROP SEQUENCE statement removes a sequence.

Invalidated objects can be re-validated when an object that has same schema and object name is created.



<a name="loio20d7a85b751910149482f673a4789209__section_o1k_1xq_xrb"/>

## Permissions

You must have the DROP object privilege on the sequence or the schema in which the sequence is located.



<a name="loio20d7a85b751910149482f673a4789209__sql_drop_sequence_1sql_drop_sequence_examples"/>

## Example

Create a sequence named seq.

```
CREATE SEQUENCE seq START WITH 11;
```

Drop the sequence named seq.

```
DROP SEQUENCE seq;
```

