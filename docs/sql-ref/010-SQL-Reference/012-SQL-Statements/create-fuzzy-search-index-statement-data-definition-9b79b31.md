<!-- loio9b79b31dde1b4f6d84144fba8d942bd3 -->

# CREATE FUZZY SEARCH INDEX Statement \(Data Definition\)

Create a fuzzy search index on NVARCHAR and NCLOB columns.



Syntax

```
CREATE FUZZY SEARCH INDEX <index_name> ON <table_name> 
   ( <column_name> ) SEARCH MODE <search_mode>
```

```
<search_mode> ::= 
  STRING
  | TEXT
  | ALPHANUM
  | IDENTIFER
  | ALPHANUM_IDENTIFIER
  | POSTCODE
```



<a name="loio9b79b31dde1b4f6d84144fba8d942bd3__sql_create_function_1sql_create_function_description"/>

## Description

Fuzzy search indexes are used to make a fuzzy search faster and they can be created for some of the SQL types that are supported by fuzzy search. The additional fuzzy search index increases the total memory footprint of a table, but it can significantly reduce the CPU times needed for a fuzzy search.

The DROP INDEX and RENAME INDEX statements can be used to managed fuzzy search indexes.

NCLOB columns support search mode TEXT only.



<a name="loio9b79b31dde1b4f6d84144fba8d942bd3__section_hl3_yhh_5rb"/>

## Permissions

Requires INDEX object privilege on the affected table to create an index.

