<!-- loio9b79b31dde1b4f6d84144fba8d942bd3 -->

# CREATE FUZZY SEARCH INDEX Statement \(Data Definition\)

Create a fuzzy search index on NVARCHAR and NCLOB columns.



Syntax

```
CREATE FUZZY SEARCH INDEX <index_name> ON <table_name> ( <column_name> ) 
   { <non_text_mode> | <text_mode> }
```



<a name="loio9b79b31dde1b4f6d84144fba8d942bd3__section_k3n_rsq_y1c"/>

## Syntax Elements


<dl>
<dt><b>

*<non\_text\_mode\>*

</b></dt>
<dd>

Specifies the available non-text search modes.

```
<non_text_mode> ::= 
   SEARCH MODE { STRING
      | TEXT
      | ALPHANUM
      | IDENTIFER
      | ALPHANUM_IDENTIFIER
      | POSTCODE }
```



</dd><dt><b>

*<text\_mode\>*

</b></dt>
<dd>

Specifies the available text search modes.

```
<text_mode> ::=
   SEARCH MODE TEXT [ TOKEN SEPARATORS { <string_literal> ] [ MIME TYPE <string_literal> ]
```



</dd>
</dl>



<a name="loio9b79b31dde1b4f6d84144fba8d942bd3__sql_create_function_1sql_create_function_description"/>

## Description

Fuzzy search indexes are used to make a fuzzy search faster and they can be created for some of the SQL types that are supported by fuzzy search. The additional fuzzy search index increases the total memory footprint of a table, but it can significantly reduce the CPU times needed for a fuzzy search.

The DROP INDEX and RENAME INDEX statements can be used to managed fuzzy search indexes.



<a name="loio9b79b31dde1b4f6d84144fba8d942bd3__section_hl3_yhh_5rb"/>

## Permissions

Requires INDEX object privilege on the affected table to create an index.



<a name="loio9b79b31dde1b4f6d84144fba8d942bd3__section_tws_b2r_y1c"/>

## Examples

This example creates fuzzy search index idx using the MIME TYPE option on column COL1 in table T1.

```
CREATE FUZZY SEARCH INDEX idx ON T1(COL1) MIME TYPE 'application/x-abap-rawstring' TOKEN SEPARATORS '\/;,.:-_()[]<>!?*@+{}="&#$~|';
```

**Related Information**  


[Fuzzy Search Indexes](https://help.sap.com/viewer/05c9edaee7fe4d28ab3627d0b1583df6/2024_3_QRC/en-US/79cbd8c7ec3340848e0654c67b45bc00.html "Fuzzy search indexes are used to make a fuzzy search faster and they can be created for some of the SQL types that are supported by fuzzy search. The additional fuzzy search index increases the total memory footprint of a table, but it can significantly reduce the CPU time needed for a fuzzy search.") :arrow_upper_right:

