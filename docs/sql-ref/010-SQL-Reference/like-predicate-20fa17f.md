<!-- loio20fa17f375191014a4d8d8cbfddfe340 -->

# LIKE Predicate

Performs a comparison to see if a character string matches a specified pattern.



<a name="loio20fa17f375191014a4d8d8cbfddfe340__sql_predicates_like_predicate_1sql_predicates_like_predicate_syntax"/>

## Syntax

```
<like_predicate> ::= <source_expression> [ NOT ] LIKE <pattern_expression> 
   [ ESCAPE <escape_expression> ]
```



<a name="loio20fa17f375191014a4d8d8cbfddfe340__sql_predicates_null_predicate_1sql_predicates_null_predicate_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<source\_expression\>*

</b></dt>
<dd>

Specifies the column or character string in which to search for *<pattern\_expression\>*. Specifying NOT inverts the operation of the LIKE predicate.



</dd><dt><b>

*<pattern\_expression\>*

</b></dt>
<dd>

Specifies the pattern to search for in *<source\_expression\>*.



</dd><dt><b>

*<escape\_expression\>*

</b></dt>
<dd>

Specifies the escape character used in comparison string *<pattern\_expression\>*, if any.



</dd>
</dl>



<a name="loio20fa17f375191014a4d8d8cbfddfe340__sql_predicates_like_predicate_1sql_predicates_like_predicate_description"/>

## Description

The LIKE predicate performs string comparisons: *<source\_expression\>* is tested for the pattern contained in *<pattern\_expression\>*. LIKE returns true if the value of *<pattern\_expression\>* is found in *<source\_expression\>* \(assuming NOT is not set\).

Wildcard characters \( % \) and \( \_ \) can be used in *<pattern\_expression\>*. The percentage sign \(%\) wildcard matches zero or more characters. The underscore \(\_\) wildcard matches exactly one character.

To match a percentage sign or underscore with the LIKE predicate, an escape character must be placed in front of the wildcard character. Use ESCAPE *<escape\_expression\>* to specify the escape character you are using. For example, `LIKE 'data_%' ESCAPE '_'` matches the string ***data%***, and `LIKE 'data__%' ESCAPE '_'` \(that is, two underscores, followed by a percent sign\) matches a string that starts with ***'data\_'***

The underscore \( \_ \) and percentage sign \( % \) are ASCII characters.

An expression is either a simple expression such as a character, a date or a number, or it can be a scalar subquery.

If any of *<source\_expression\>*, *<pattern\_expression\>*, or *<escape\_expression\>* is NULL, then the predicate returns UNKNOWN.

**Related Information**  


[Expressions](expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Expressions](expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

