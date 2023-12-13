<!-- loio4114b026f750429c8eeef9f54258edfa -->

# OCCURRENCES\_REGEXPR Function \(String\)

Returns the number of matches of a regular expression search within a string.



## Syntax

```
OCCURRENCES_REGEXPR( <pattern> [ FLAG <flag> ] IN <regex_subject_string> [ FROM <start_position> ] )
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

Specifies the matching behavior of the function and can be defined by the flag literal.

```
<flag> ::= { 'i' | 'm' | 's' | 'x' }
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

Specifies the string to search within. If *<regex\_subject\_string\>* is empty, then the result is empty.

```
<regex_subject_string> ::= <string>
```



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

Specifies a positive integer that indicates the character of *<regex\_subject\_string\>* where the search is started. If *<start\_position\>* is not a positive integer, then -1 is returned.

```
<start_position> ::= <positive_integer>
```



</dd>
</dl>



## Description

Returns the number of matches of a regular expression search within a string.



## Example

The following example returns the number of occurrences of digits in the specified string, `'a1b2'`, and returns the value ***2***:

```
SELECT OCCURRENCES_REGEXPR('([[:digit:]])' IN 'a1b2') "occurrences_regexpr" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

