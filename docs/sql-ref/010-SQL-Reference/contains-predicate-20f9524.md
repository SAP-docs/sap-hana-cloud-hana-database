<!-- loio20f952437519101487edc3d9aba84238 -->

# CONTAINS Predicate

Matches a search string with the results of a subquery.



## Syntax

```
<contains_predicate> ::= CONTAINS ( 
 <contains_columns>, 
 <search_string> 
 [, <search_specifier>] )
```



## Syntax Elements


<dl>
<dt><b>

*<contains\_columns\>*

</b></dt>
<dd>

Specifies the columns to search.

```
<contains_columns> ::= 
 * 
 | <column_name> 
 | ( <column_list> )

<column_list> ::=
( <column_name> [,<..>] )
```



</dd><dt><b>

*<search\_string\>*

</b></dt>
<dd>

Specifies the string to search for in *<contains\_columns\>*, using the freestyle search string format \(for example, Peter "Palo Alto" OR Berlin -"SAP LABS"\).

```
<search_string> ::= <string_const>
```



</dd><dt><b>

*<search\_specifier\>*

</b></dt>
<dd>

Defines specifications on the type of matching to perform. If *<search\_specifier\>* is not specified, EXACT is the default.

```
<search_specifier><search_type>] [  ::= 
 [<opt_search_specifier2_list>]
 | <search_specifier2_list>
 
<opt_search_specifier2_list> ::= 
 (empty, nothing specified)
 | <search_specifier2_list>
 
<search_type> ::= 
 <exact_search> 
 | <fuzzy_search>
<search_specifier2_list> ::= 
 <search_specifier2>
 | <search_specifier2_list> , <search_specifier2>
 
<search_specifier2> ::=  
 <weights> 
 
<exact_search> ::= 
 EXACT 
 | EXACT ( <additional_params> )
  
<fuzzy_search>  ::=  ::= 
 FUZZY 
 | FUZZY ( <fuzzy_params> ) 
 | FUZZY ( <fuzzy_params_list> )

<fuzzy_params_list>  ::= ( <fuzzy_params> ) , <fuzzy_params_list2>

<fuzzy_params_list2> ::= 
 ( <fuzzy_params> ) 
 | <fuzzy_params_list2> , ( <fuzzy_params> )
 
<fuzzy_params> ::= 
 <float_const> 
 | <float_const> , <additional_params> 
 | NULL , <additional_params>


 <weights> ::= WEIGHT ( <float_const_list> )
 

 <additional_params> ::= <string_const>
```


<dl>
<dt><b>

FUZZINESSTHRESHOLD

</b></dt>
<dd>

If the FUZZINESSTHRESHOLD parameter is defined in a join view, and *<search\_specifier\>* is not specified, a fuzzy search is performed using the fuzziness threshold defined in the view.



</dd><dt><b>

EXACT

</b></dt>
<dd>

Specifies to match the term or phrase exactly.

EXACT returns records where exact matches of the search terms are found in the search attributes.



</dd><dt><b>

FUZZY

</b></dt>
<dd>

Specifies to return matches that are similar to *<search\_string\>* \(spelling errors are ignored to a certain extent for example\).

Optionally, you can control the degree of fuzziness using parameters. For example, *<float\_const\>* specifies the degree of fuzziness expressed as value between 0.0 and 1.0, where 0.0 is very fuzzy, and 1.0 is exact. If *<float\_const\>* is not specified, 0.8 is the default. It is possible to override this default by defining parameter FUZZINESSTHRESHOLD supported by columnstore join views.

When FUZZY is specified with more than one *<additional\_params\>* parameter, the number of *<float\_const\>* / *<additional\_params\>* pairs must match the number of column names in the column list.



</dd><dt><b>

*<additional\_params\>*

</b></dt>
<dd>

Specifies additional search parameters in the format of key-value pairs.



</dd><dt><b>

WEIGHT

</b></dt>
<dd>

Specifies weightings for the columns. If a weights list is specified, it must be the same size as the number of \(expanded\) columns in *<contains\_columns\>*.



</dd>
</dl>



</dd>
</dl>



## Remarks

The CONTAINS predicate only works on column store objects \(column tables and attribute views\).

If there are multiple CONTAINS predicates specified in the WHERE clause of a SELECT statement, only one of the predicates can consist of more than one column in the *<contains\_columns\>* list.



## Examples

The following example performs a fuzzy search for the term `cap`, and returns the rows that match \(`Blue baseball cap`, and `Red car`\), in descending order by score:

```
CREATE SCHEMA mySchema;
CREATE COLUMN TABLE mySchema.SEARCH_TEXT( Content VARCHAR(20), Descrip VARCHAR(20), Comment VARCHAR(20) );
INSERT INTO mySchema.SEARCH_TEXT VALUES( 'Blue baseball cap', 'Vintage', 'Out of stock');  
INSERT INTO mySchema.SEARCH_TEXT VALUES( 'Red car', 'Vintage', 'Taking orders' );  
INSERT INTO mySchema.SEARCH_TEXT VALUES( 'Bluish sky', 'Retro', 'Discontinued' );

SELECT SCORE() AS SCORE,*  
   FROM mySchema.SEARCH_TEXT  
   WHERE CONTAINS(CONTENT,'cap',FUZZY(0.0))  
   ORDER BY SCORE DESC;
```

Changing SELECT statement to set the FUZZY parameter to `0.9`, the equivalent of making the query less fuzzy or more exact, returns only the `Blue baseball cap` row:

```
SELECT SCORE() AS SCORE,*  
   FROM mySchema.SEARCH_TEXT  
   WHERE CONTAINS(CONTENT,'cap',FUZZY(0.9))  
   ORDER BY SCORE DESC
```

Using the table created in the previous example, the following statement performs an exact term search for either `cap` or `sky`, and returns the `Blue baseball cap` and `Bluish sky` rows:

```
SELECT * FROM mySchema.SEARCH_TEXT WHERE CONTAINS(CONTENT,'cap OR sky');
```

The following statement performs an exact phrase search for either `baseball cap` and returns the `Blue baseball cap` row:

```
SELECT * FROM mySchema.SEARCH_TEXT WHERE CONTAINS(CONTENT, '"baseball cap"');
```

The following statements demonstrate ways to perform a freestyle search over multiple columns. The second example is particularly helpful when you want to search across an entire table without listing the rows.

```
SELECT * FROM mySchema.SEARCH_TEXT WHERE CONTAINS (( Content, Descrip ), 'vintage');
SELECT * FROM mySchema.SEARCH_TEXT WHERE CONTAINS (*, 'vintage');
```

**Related Information**  


[Search with SQL](https://help.sap.com/viewer/05c9edaee7fe4d28ab3627d0b1583df6/2024_3_QRC/en-US/cd07da82bb571014b185c8e3e3974767.html "In column-oriented tables, you can perform searches using the SQL SELECT statement.") :arrow_upper_right:

[SCORE Function \(Miscellaneous\)](011-SQL-Functions/score-function-miscellaneous-20e6f8e.md "Returns the relevance of a record that has been found.")

