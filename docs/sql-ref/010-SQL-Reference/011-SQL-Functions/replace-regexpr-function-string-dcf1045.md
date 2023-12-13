<!-- loiodcf1045ce51d45119cfe8ba17cf9da4f -->

# REPLACE\_REGEXPR Function \(String\)

Searches a string for a regular expression pattern and returns the string with either one or every occurrence of the regular expression pattern that is replaced using a replacement string.



## Syntax

```
REPLACE_REGEXPR(<pattern> [ FLAG <flag> ] 
 IN <regex_subject_string> 
 [ WITH <replacement_string> ] 
 [ FROM <start_position> ] 
 [ OCCURRENCE <regex_replace_occurrence> ])
```



## Syntax Elements


<dl>
<dt><b>

*<pattern\>*

</b></dt>
<dd>

Specifies a search pattern based on Perl Compatible Regular Expression \(PCRE\).

```
<pattern> ::= !!Perl Compatible Regular Expression
```



</dd><dt><b>

*<flag\>*

</b></dt>
<dd>

Specifies the matching behavior to use.

```
<flag> ::= 'i' | 'm' | 's' | 'x'
```

**Flag options**


<table>
<tr>
<th valign="top">

Flag option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

i

</td>
<td valign="top">

Enables case-insensitive matching

</td>
</tr>
<tr>
<td valign="top">

m

</td>
<td valign="top">

Enables multiline mode, where the *<subject\_string\>* will be treated as multiple lines and the expression ^ and $ match just after or just before, respectively, a line terminator or the end of the input sequence

</td>
</tr>
<tr>
<td valign="top">

s

</td>
<td valign="top">

Enables the expression *<.\>* as a wildcard to match any character, including a line terminator

</td>
</tr>
<tr>
<td valign="top">

x

</td>
<td valign="top">

Permits whitespace and comments in the pattern

</td>
</tr>
<tr>
<td valign="top">

U

</td>
<td valign="top">

SAP HANA uses the Perl-compatible Regular Expressions \(PCRE\) library to process regular expressions. Specifying 'U' \(short for "ungreedy"\) inverts the "greediness" of quantifiers so that they are not greedy by default but become greedy only when followed by "?". Ungreedy matching can often perform faster because it finds the shorter match at times when it is only interesting to know whether there is any match.

For a full understanding of the "greedy" versus "ungreedy" matching behavior of the Perl-compatible Regular Expressions \(PCRE\) library, visit:[https://www.pcre.org/original/doc/html/pcrematching.html](https://www.pcre.org/original/doc/html/pcrematching.html) .

</td>
</tr>
</table>



</dd><dt><b>

*<regex\_subject\_string\>*

</b></dt>
<dd>

Specifies the string that the search pattern should be applied to. If *<regex\_subject\_string\>* is empty, the result is empty.

```
<regex_subject_string> ::= <string_literal>
```



</dd><dt><b>

*<replacement\_string\>*

</b></dt>
<dd>

Specifies the string that replaces all occurrences found by the function. The default is an empty string.

```
<replacement_string> ::= <string_literal>
```



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

Specifies the character of *<regex\_subject\_string\>* where the search is started, if the value is a positive integer. Otherwise, NULL is returned.

```
<start_position> ::= <numeric_literal>
```



</dd><dt><b>

*<regex\_replace\_occurrence\>*

</b></dt>
<dd>

Specifies a non-negative integer or ALL, and indicates the occurrence of the replace operation. If *<regex\_replace\_occurrence\>* is a negative integer, then the *<regex\_subject\_string\>* is returned without any change. The default value is ALL.

```
<regex_replace_occurrence> ::= <numeric_literal> | ALL 
```



</dd>
</dl>



## Description

Searches a string for a regular expression pattern and returns the string with either one or every occurrence of the regular expression pattern that is replaced using a replacement string.

If any of the following parameters is NULL, then the function returns NULL: *<pattern\>*, *<flag\>*, *<regex subject\_string\>*, *<replacement\_string\>*, *<start\_position\>* or *<regex\_replace\_occurrence\>*.



## Example

The following example uses a regular expression to replace date format `2014-04-01` with the value ***01/04/2014***:

```
SELECT REPLACE_REGEXPR('([[:digit:]]{4})-([[:digit:]]{2})-([[:digit:]]{2})' IN '2014-04-01' 
WITH '\3/\2/\1' OCCURRENCE ALL) "replace_regexpr" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

