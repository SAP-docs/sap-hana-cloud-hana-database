<!-- loio20e6f8e97519101489a0cd3c29991e72 -->

# SCORE Function \(Miscellaneous\)

Returns the relevance of a record that has been found.



<a name="loio20e6f8e97519101489a0cd3c29991e72__sql_function_score_1sql_function_score_syntax"/>

## Syntax

Syntax 1 - Without Parameters

```
SCORE()
```

Syntax 2 - With Parameters

```
SCORE ( <search_string> IN <score_columns> )
```



<a name="loio20e6f8e97519101489a0cd3c29991e72__section_ncj_ncr_kwb"/>

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
   | LINEAR <linear_scoring_details>
   | GAUSSIAN <gaussian_scoring_details>
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
   | COMPOUND WORD WEIGHT <value_range_2>
   | NON MATCHING TOKEN MODE {'max' | 'min' | 'all' | 'input' | 'table'}
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
   | COMPOUND WORD WEIGHT <value_range_2>
   | NON MATCHING TOKEN MODE {'max' | 'min' | 'all' | 'input' | 'table'}
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

A value that is \>= 0.0 or <= 1. For example, 0.326, 0.57, or 0.9.



</dd><dt><b>

*<value\_range\_2\>*

</b></dt>
<dd>

A value where n \> 0 and n < 1.0.



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

```

```



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

*<linear\_scoring\_details\>*

</b></dt>
<dd>

```
<scoring_details> ::=
   [ MINIMAL SCORE <value_range> ] 
   [ OFFSET { 0 | <positive_float_constant> ] 
   [ DECAY <linear_decay_value> ] 
   SCALE <positive_float_constant>
   [ SEARCH MODE { 'date' | 'numc' }
   [ WEIGHT <weight_value> ]
```



</dd><dt><b>

*<gaussian\_scoring\_details\>*

</b></dt>
<dd>

```
<scoring_details> ::=
   [ MINIMAL SCORE <value_range> ] 
   [ OFFSET { 0 | <positive_float_constant> ] 
   [ DECAY <gaussian_decay_value> ] 
   SCALE <positive_float_constant>
   [ SEARCH MODE { 'date' | 'numc' }
   [ WEIGHT <weight_value> ]
```



</dd><dt><b>

*<linear\_decay\_value\>*

</b></dt>
<dd>

A value greater than or equal to 0.0 but less than 1.0.



</dd><dt><b>

*<gaussian\_decay\_value\>*

</b></dt>
<dd>

A value greater than 0.0 but less than 1.0.



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
   [ OFFSET { 0 | <float_constant> ] 
   [ BASE <float_constant> ]
   [ SEARCH MODE 'numc' ]
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
   ( <column_name> [ , <column_name> ],...] )
```



</dd><dt><b>

*<specific\_columns\_same\_options\>*

</b></dt>
<dd>

```
<specific_columns_same_options>  ::= 
   ( <column_name> [, <column_name> ],...] ) [ <scoring_type> ]
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



<a name="loio20e6f8e97519101489a0cd3c29991e72__sql_function_score_1sql_function_score_description"/>

## Description

**Syntax 1** can only be used in search queries using the CONTAINS predicate. Use SCORE to obtain the relevance of a record that has been found. SCORE returns a real value between 0 and 1. The SAP HANA database calculates a score based on the following information:

-   The relevance, or weighting, of attributes in a search using the CONTAINS predicate. The relevance of a match depends on the weight of the column that caused the match. You can specify weights as you create the view, or in the CONTAINS predicate.

-   Fuzziness in a fuzzy search. The more exact matching that occurs, the higher the score is.


**Syntax 2** cannot be used with the CONTAINS predicate. It replaces Syntax 1.



<a name="loio20e6f8e97519101489a0cd3c29991e72__sql_function_score_1sql_function_score_examples"/>

## Examples



<a name="loio20e6f8e97519101489a0cd3c29991e72__section_pqs_tkd_nwb"/>

## Syntax 1

The following example creates a table that contains a string and adds a fuzzy text index to it.

```
CREATE TABLE T1 (CONTENT NCLOB MEMORY THRESHOLD NULL);
CREATE FUZZY SEARCH INDEX IDX1 ON T1(CONTENT) SEARCH MODE TEXT;
```

```
INSERT INTO T1 VALUES('This is a test.');
```

Use the SCORE function to check the table contents for relevance against the search string 'is':

```
SELECT SCORE(), CONTENT FROM T1 WHERE CONTAINS(CONTENT, 'is', EXACT('searchMode=text')); 
```


<table>
<tr>
<th valign="top">

SCORE



</th>
<th valign="top">

CONTENT



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

This is a test.



</td>
</tr>
<tr>
<td valign="top">

0.40833336114883423



</td>
<td valign="top">

This was a test.



</td>
</tr>
</table>

Still using TABLE T1, the following example adds additional values to the table.

```
INSERT INTO T1 VALUES('example');
INSERT INTO T1 VALUES('examples');
```

Use the SCORE function to check the table contents for similarity to the string 'example':

```
SELECT SCORE(), CONTENT FROM T1 WHERE CONTAINS(CONTENT, 'example',FUZZY(0.8, 'searchMode=text'));
```


<table>
<tr>
<th valign="top">

SCORE



</th>
<th valign="top">

CONTENT



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

example



</td>
</tr>
<tr>
<td valign="top">

0.9527000188827515



</td>
<td valign="top">

examples



</td>
</tr>
</table>



<a name="loio20e6f8e97519101489a0cd3c29991e72__section_umx_skd_nwb"/>

## Syntax 2

The following example creates a table that contains a string and adds a fuzzy text index to it:

```
CREATE TABLE T2 (CONTENT NCLOB MEMORY THRESHOLD NULL);
CREATE FUZZY SEARCH INDEX IDX2 ON T2(CONTENT) SEARCH MODE TEXT;
```

```
INSERT INTO T2 VALUES('This is a test.');
```

Use the SCORE function to check the table contents for relevance against the search string 'is':

```
SELECT SCORE('is' IN CONTENT EXACT SEARCH MODE 'text') AS SCORE, CONTENT FROM T2 WHERE SCORE('is' IN CONTENT EXACT SEARCH MODE 'text') > 0.2;
```


<table>
<tr>
<th valign="top">

SCORE



</th>
<th valign="top">

CONTENT



</th>
</tr>
<tr>
<td valign="top">

1


</td>
<td valign="top">

This is a test.



</td>
</tr>
</table>

Still using TABLE T2, the following example adds additional values to the table.

```
INSERT INTO T2 VALUES('example');
INSERT INTO T2 VALUES('examples');
```

Use the SCORE function to check the table contents for similarity to the string 'example':

```
SELECT SCORE('example' IN CONTENT FUZZY MINIMAL SCORE 0.8 MINIMAL TOKEN SCORE 0.8 SEARCH MODE 'text') AS SCORE, CONTENT FROM T2
WHERE SCORE('example' IN CONTENT FUZZY MINIMAL SCORE 0.8 MINIMAL TOKEN SCORE 0.8 SEARCH MODE 'text') > 0.8;
```


<table>
<tr>
<th valign="top">

SCORE



</th>
<th valign="top">

CONTENT



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

example



</td>
</tr>
<tr>
<td valign="top">

0.9527000188827515



</td>
<td valign="top">

examples



</td>
</tr>
</table>

