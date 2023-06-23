<!-- loio20d9c05f75191014b24fca55a8534531 -->

# DROP VIEW Statement \(Data Definition\)

Removes a view from the database.





<a name="loio20d9c05f75191014b24fca55a8534531__sql_drop_view_1sql_drop_view_syntax"/>

## Syntax

```
DROP VIEW <view_name> [<drop_option>]
```



<a name="loio20d9c05f75191014b24fca55a8534531__sql_drop_view_1sql_drop_view_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<view\_name\>*

</b></dt>
<dd>

Drops the specified view, with the optional schema name.

```
<view_name> ::= [ <schema_name>. ]<identifier>

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

CASCADE drops the view and dependent objects. RESTRICT drops the view only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.

If *<drop\_option\>* is not specified, then a non-cascaded drop is performed which only drops the specified view. Dependent objects of the view are invalidated but not dropped.

The invalidated objects can be re-validated when an object that has same schema and object name is created.



</dd>
</dl>



<a name="loio20d9c05f75191014b24fca55a8534531__sql_drop_view_1sql_drop_view_description"/>

## Description

The DROP VIEW statement removes a view from the database.

Dropping a view also drops any expression macros defined for the view. The list of all expression macros for a view can be obtained by querying the VIEW\_EXPRESSION\_MACROS system view.



<a name="loio20d9c05f75191014b24fca55a8534531__sql_drop_view_1sql_drop_view_examples"/>

## Example

Create table t, and then a view, v, that selects all records from table t.

```
CREATE ROW TABLE t (a INT);
 CREATE VIEW v AS SELECT * FROM t;
```

Drop view v from the database.

```
DROP VIEW v;
```

**Related Information**  


[VIEW\_EXPRESSION\_MACROS System View](../../020-System-Views-Reference/021-System-Views/view-expression-macros-system-view-d163421.md "Describes the expression macros defined for views.")

