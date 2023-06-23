<!-- loio20d7e172751910148bccb49de92d9859 -->

# DROP SYNONYM Statement \(Data Definition\)

Removes a synonym.



<a name="loio20d7e172751910148bccb49de92d9859__sql_drop_synonym_1sql_drop_synonym_syntax"/>

## Syntax

```
DROP [PUBLIC] SYNONYM <synonym_name> [<drop_option>]
```



<a name="loio20d7e172751910148bccb49de92d9859__sql_drop_synonym_1sql_drop_synonym_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

PUBLIC

</b></dt>
<dd>

Allows the removal of a public synonym.



</dd><dt><b>

SYNONYM *<synonym\_name\>*

</b></dt>
<dd>

Drops the specified synonym, with the optional schema name.

```
<synonym_name> ::= [<schema_name>.]<identifier>

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

CASCADE drops the synonym and dependent objects. RESTRICT drops the synonym only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.

If *<drop\_option\>* is not specified, then a non-cascaded drop is performed which only drops the specified synonym. Dependent objects of the synonym are invalidated but not dropped.

The invalidated object can be re-validated when an object that has same schema and object name is created.



</dd>
</dl>



<a name="loio20d7e172751910148bccb49de92d9859__sql_drop_synonym_1sql_drop_synonym_description"/>

## Description

The DROP SYNONYM statement removes a synonym.



<a name="loio20d7e172751910148bccb49de92d9859__section_twj_1xx_vcb"/>

## Permissions

Only database users with DROP object privilege on the remote source can drop a synonym from a remote source.



<a name="loio20d7e172751910148bccb49de92d9859__sql_drop_synonym_1sql_drop_synonym_examples"/>

## Example

Create a table a, then a synonym, a\_synonym, and a public synonym, pa\_synonym, for the table.

```
CREATE ROW TABLE a (c INT);
 CREATE SYNONYM a_synonym FOR a;
 CREATE PUBLIC SYNONYM pa_synonym FOR a;
```

Drop both the synonym a\_synonym and public synonym pa\_synonym using a non-cascaded drop in both cases.

```
DROP SYNONYM a_synonym;
 DROP PUBLIC SYNONYM pa_synonym;
```

