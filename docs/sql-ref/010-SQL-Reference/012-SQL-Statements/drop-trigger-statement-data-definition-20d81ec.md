<!-- loio20d81ec9751910148fe6e1e072ac439e -->

# DROP TRIGGER Statement \(Data Definition\)

Deletes a trigger.



<a name="loio20d81ec9751910148fe6e1e072ac439e__sql_drop_trigger_1sql_drop_trigger_syntax"/>

## Syntax

```
DROP TRIGGER <trigger_name> [ <drop_option> ] [ ONLINE ]
```



<a name="loio20d81ec9751910148fe6e1e072ac439e__sql_drop_trigger_1sql_drop_trigger_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<trigger\_name\>*

</b></dt>
<dd>

Drops the specified trigger, with the optional schema name.

```
<trigger_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= CASCADE | RESTRICT
```

CASCADE drops the trigger and dependent objects. RESTRICT drops the trigger only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.

If *<drop\_option\>* is not specified, then a non-cascaded drop is performed, which only drops the specified trigger. Dependent objects of the trigger are invalidated but not dropped.



</dd><dt><b>

ONLINE

</b></dt>
<dd>

Applies an intentional exclusive lock \(instead of an exclusive lock\) before performing the operation. An intentional exclusive lock differs from the default lock \(exclusive\) because it allows concurrent DML and DDL related to the object to proceed, and will retry the operation until it can proceed.

ONLINE applies an intentional exclusive lock only if the auto commit mode for DDL statements is set to on. If the auto commit mode for DDL statement is not set to on, then an exclusive lock is still applied.



</dd>
</dl>



<a name="loio20d81ec9751910148fe6e1e072ac439e__sql_drop_trigger_1sql_drop_trigger_description"/>

## Description

Invalidated objects can be re-validated when an object that has same schema and object name is created.



<a name="loio20d81ec9751910148fe6e1e072ac439e__section_dwy_dkm_wcb"/>

## Permissions

Only database users with the TRIGGER privilege for the table on which the trigger was defined are allowed to drop a trigger for that table.



<a name="loio20d81ec9751910148fe6e1e072ac439e__sql_drop_trigger_1sql_drop_trigger_examples"/>

## Example

Create two tables, `target` and `sample`, and a trigger called `test`.

```
CREATE ROW TABLE target ( A INT);
 CREATE ROW TABLE sample ( A INT);
 CREATE TRIGGER test
 AFTER UPDATE ON target
 BEGIN  
   INSERT INTO sample VALUES(3);
 END;
```

Drop the trigger called test.

```
DROP TRIGGER test;
```

Alternatively, you can drop the trigger and specify ONLINE so that the operation proceeds only when concurrent DML or DDL finishes.

```
DROP TRIGGER test ONLINE;
```

