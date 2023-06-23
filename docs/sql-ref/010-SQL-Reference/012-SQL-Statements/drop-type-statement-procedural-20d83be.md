<!-- loio20d83beb751910148651cebdf3564ad3 -->

# DROP TYPE Statement \(Procedural\)

Removes a user-defined table type.



<a name="loio20d83beb751910148651cebdf3564ad3__sql_drop_type_1sql_drop_type_syntax"/>

## Syntax

```
DROP TYPE <type_name> [<drop_option>]
```



<a name="loio20d83beb751910148651cebdf3564ad3__sql_drop_type_1sql_drop_type_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<type\_name\>*

</b></dt>
<dd>

Specifies the table type to be dropped with optional schema name.

```
<type_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the desired drop behavior.

```
<drop_option> ::= CASCADE | RESTRICT
```

The default behavior is to drop only the specified table type, regardless of dependencies. When RESTRICT is specified, an error is returned if there are any objects \(currently only tables are supported\) that are dependent on the type. When CASCADE is specified, both the specified type and any dependent objects are dropped. For example, assume there is a type T being used by a database object O:

-   DROP TYPE T - Only type T is dropped; object O becomes invalid.

-   DROP TYPE T RESTRICT - The drop operation fails and an error is returned \(because O is dependent on type T\).

-   DROP TYPE T CASCADE - Both type T and object O are dropped.




</dd>
</dl>



<a name="loio20d83beb751910148651cebdf3564ad3__sql_drop_type_1sql_drop_type_description"/>

## Description

The DROP TYPE statement removes a user-defined table type.

To find invalid objects in the database, look at the IS\_VALID columns in the relevant system view. For example, you can look at the IS\_VALID column of the TABLES system view to determine which tables are valid.

Invalidated objects can be revalidated when an object that has same schema and object name is created.



<a name="loio20d83beb751910148651cebdf3564ad3__sql_drop_type_1sql_drop_type_examples"/>

## Example

Create a table type called my\_type.

```
CREATE TYPE "my_type" AS TABLE ( "column_a" DOUBLE );
```

Drop the my\_type table type.

```
DROP TYPE "my_type";
```

