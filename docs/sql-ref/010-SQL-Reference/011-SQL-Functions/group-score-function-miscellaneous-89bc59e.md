<!-- loio89bc59e4df254c29b66f8feed2b785dc -->

# GROUP\_SCORE Function \(Miscellaneous\)

Returns the relevance of a record that has been found.



<a name="loio89bc59e4df254c29b66f8feed2b785dc__sql_function_score_1sql_function_score_syntax"/>

## Syntax

```
GROUP_SCORE ( <search_string> IN <score_columns> )
```



<a name="loio89bc59e4df254c29b66f8feed2b785dc__section_ncj_ncr_kwb"/>

## Syntax Elements


<dl>
<dt><b>

*<score\_columns\>*

</b></dt>
<dd>

```
<score_columns> ::= 
   { <single_column>
   | <specific_columns_diff_options>
   | <specific_columns_same_options>
   | <all_colums> }
```


<dl>
<dt><b>

*<single\_column\>*

</b></dt>
<dd>

```
<single_column> ::= 
   <column_name> [ <scoring_type> ]
```



</dd><dt><b>

*<scoring\_type\>*

</b></dt>
<dd>

```
<scoring_type> ::= 
   { EXACT [ <exact_options> ]
   | FUZZY [ <fuzzy_options> ]
   | LINEAR <scoring_details>
   | GAUSSIAN <scoring_details>
   | LOGARITHMIC <logarithmic_scoring_details> }
```


<dl>
<dt><b>

*<exact\_options\>*

</b></dt>
<dd>

```
<exact_options> :: 
   { AND THRESHOLD <value_range>
   | MINIMAL SCORE <value_range>
   | WEIGHT <value_range_2>
   | COMPOSE WORDS <positive_integer_constant>
   | COMPOUND WORD WEIGHT <value_range_2>
   | NON MATCHING TOKEN MODE {'max' | 'min' | 'all' | 'input' | 'table'}
   | DECOMPOSE WORDS <positive_integer_constant>
   | EXCESS TOKEN WEIGHT <value_range>
   | SEARCH MODE <search_mode> }
```



</dd><dt><b>

*<fuzzy\_search\>*

</b></dt>
<dd>

```
<fuzzy_options> ::=
   { AND THRESHOLD <value_range>
   | AND THRESHOLD <value_range>
   | MINIMAL SCORE <value_range>
   | WEIGHT <value_range_2>
   | COMPOSE WORDS <positive_integer_constant>
   | COMPOUND WORD WEIGHT <value_range_2>
   | NON MATCHING TOKEN MODE {'max' | 'min' | 'all' | 'input' | 'table'}
   | DECOMPOSE WORDS <positive_integer_constant>
   | ERROR DEVALUATE <value_range>
   | EXCESS TOKEN WEIGHT <value_range>
   | SUBSTRING MATCH { 'off' | 'anywhere' | 'beginning' }
   | LANGUAGE TRANSLATION {'on' | 'off'}
   | LENGTH TOLERANCE  <value_range>
   | MAX DATE DISTANCE { 0 | <positive_integer_constant> }
   | MINIMAL SEARCH LENGTH { 0 | <positive_integer_constant>
   | SEARCH MODE <search_mode>
   | SIMILARITY CALCULATION MODE <similar_calculation_mode>
   | SPELL CHECK FACTOR <value_range>
   | MINIMAL TOKEN SCORE  <value_range> }
```



</dd><dt><b>

*<value\_range\_1\>*

</b></dt>
<dd>

A value that is greater than or equal to 0.0 and less than or equal to 1. For example, 0.326, 0.57, or 0.9.



</dd><dt><b>

*<value\_range\_2\>*

</b></dt>
<dd>

A value that is greater than 0 and less than 1.0.



</dd><dt><b>

*<positive\_float\_constant\>*

</b></dt>
<dd>

A positive integer greater than 1.0. For example, 57.326.



</dd><dt><b>

*<positive\_integer\_constant\>*

</b></dt>
<dd>

A positive integer constant. For example, 5.



</dd><dt><b>

*<float\_constant\>*

</b></dt>
<dd>

A non-negative value.



</dd><dt><b>

*<search\_mode\>*

</b></dt>
<dd>

```
<search_mode> ::= 
   { 'alphanum' 
   | 'alphanum identifier' 
   | 'house number' 
   | 'identifier' 
   | 'postcode' 
   | 'string' 
   | 'text'}
```



</dd><dt><b>

*<similar\_calculation\_mode\>*

</b></dt>
<dd>

```
<similar_calculation_mode> ::= 
   {'compare' 
   | 'type ahead' 
   | 'search compare' 
   | 'search' 
   | 'symmetric search' 
   | 'substring search' 
   | 'flexible'} 
```



</dd><dt><b>

*<scoring\_details\>*

</b></dt>
<dd>

```
<scoring_details> ::=
   [ MINIMAL SCORE <value_range> ] 
   [ OFFSET { 0 | <positive_float_constant> ] 
   [ DECAY <decay_value> ] 
   SCALE <positive_float_constant>
   [ SEACH MODE { 'date' | 'numc' }
   [ WEIGHT <weight_value> ]
```



</dd><dt><b>

*<decay\_value\>*

</b></dt>
<dd>

A value no less than 0.0 but less than 1.0.



</dd><dt><b>

*<weight\_value\>*

</b></dt>
<dd>

A value greater than 0.0 and less than or equal to 1.0.



</dd><dt><b>

*<logarithmic\_scoring\_details\>*

</b></dt>
<dd>

```
<logarithmic_scoring_details> ::=
   [ MINIMAL SCORE <value_range> ] 
   [ OFFSET { 0 | <positive_float_constant> ] 
   BASE <float_constant>
   [ SEACH MODE 'numc' ]
   [ WEIGHT <weight_value> ]
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<specific\_columns\_diff\_options\>*

</b></dt>
<dd>

```
<specific_columns_diff_options>  ::= 
   ( <single_column>> [ , <single_column> ]...] ) 
```



</dd><dt><b>

*<specific\_columns\_same\_options\>*

</b></dt>
<dd>

```
<specific_columns_same_options>  ::= 
   ( <single_column>> [ , <single_column> ]...] ) [ <scoring_type> ]
```



</dd><dt><b>

*<all\_columns\>*

</b></dt>
<dd>

```
<all_columns> ::= * [ <scoring_type> ]
```



</dd>
</dl>



<a name="loio89bc59e4df254c29b66f8feed2b785dc__sql_function_score_1sql_function_score_description"/>

## Description

Use GROUP\_SCORE to obtain the relevance of a group of records that have been found. GROUP\_SCORE returns a real value between 0 and 1. The SAP HANA database calculates a score based on the following information:

-   The relevance, or weighting, of attributes. The relevance of a match depends on the weight of the column that caused the match. You can specify weights as you create the view.

-   Fuzziness in a fuzzy search. The more exact matching that occurs, the higher the score is.




<a name="loio89bc59e4df254c29b66f8feed2b785dc__sql_function_score_1sql_function_score_examples"/>

## Examples

The following example creates two table that contains several strings:

```
CREATE TABLE companies (id int, name varchar(255));
INSERT INTO companies VALUES (1, 'Company One');
INSERT INTO companies VALUES (2, 'Company Two');
INSERT INTO companies VALUES (3, 'Company Three');

```

```
CREATE TABLE locations (company_id int, location nvarchar(255));
INSERT INTO locations VALUES (1, 'Berlin');
INSERT INTO locations VALUES (1, 'Seattle');
INSERT INTO locations VALUES (1, 'Tokyo');
INSERT INTO locations VALUES (2, 'Berlin');
INSERT INTO locations VALUES (2, 'Tokyo');
INSERT INTO locations VALUES (3, 'London');

```

Use the GROUP\_SCORE function to check the data for relevance against the search string 'Berlin Seattle Tokyo':

```
SELECT name, group_score('Berlin Seattle Tokyo' IN (name, location))
FROM companies JOIN locations ON id = company_id
GROUP BY name;

```

****


<table>
<tr>
<th valign="top">

NAME

</th>
<th valign="top">

group\_score\('Berlin Seattle Tokyo' IN \(name, location\)

</th>
</tr>
<tr>
<td valign="top">

Company One

</td>
<td valign="top">

1.0

</td>
</tr>
<tr>
<td valign="top">

Company Two

</td>
<td valign="top">

0.42264974

</td>
</tr>
<tr>
<td valign="top">

Company Three

</td>
<td valign="top">

0.0

</td>
</tr>
</table>

