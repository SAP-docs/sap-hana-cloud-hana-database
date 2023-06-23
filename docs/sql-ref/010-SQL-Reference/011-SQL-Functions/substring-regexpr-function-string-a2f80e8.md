<!-- loioa2f80e8ac8904c13959c69bfc3058f19 -->

# SUBSTRING\_REGEXPR Function \(String\)

Searches a string for a regular expression pattern and returns one occurrence of the matching substring.



## Syntax

```
SUBSTR[ING]_REGEXPR( <pattern> [ FLAG <flag> ] IN <regex_subject_string> 
 [ FROM <start_position> ] 
 [ OCCURRENCE <regex_occurrence> ] 
 [ GROUP <regex_capture_group> ] )
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

Specifies that the matching behavior of the function can be defined by the flag literal. The following options are available:

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

```
<flag> ::= 'i' | 'm' | 's' | 'x'
```



</dd><dt><b>

*<regex\_subject\_string\>*

</b></dt>
<dd>

Defines the string that the search pattern should be applied to. If *<regex\_subject\_string\>* is empty, then the result is empty.

```
<regex_subject_string> ::= <string>
```



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

Setting this parameter to a positive integer indicates which character of *<regex\_subject\_string\>* the search begins at. If *<start\_position\>* is not a positive integer, then NULL is returned.

```
<start_position> ::= <numeric_literal>
```



</dd><dt><b>

*<regex\_occurrence\>*

</b></dt>
<dd>

Setting this parameter to a positive integer indicates the occurrence of the *<pattern\>* in *<regex\_subject\_string\>*. The default is 1 and returns the first occurrence. If *<regex\_occurrence\>* is not a positive integer, then NULL is returned.

```
<regex_occurrence> ::= <numeric_literal >
```



</dd><dt><b>

*<regex\_capture\_group\>*

</b></dt>
<dd>

Indicates the number of the captured substring's group by the regular expression. The default is 0. If *<regex\_capture\_group\>* is a negative integer, then 0 is returned.

```
<regex_capture_group> ::= <integer>
```



</dd>
</dl>



## Description

Searches a string for a regular expression pattern and returns one occurrence of the matching substring.

If any of the following parameters is NULL, then the function returns NULL: *<pattern\>*, *<flag\>*, *<regex\_subject\_string\>*, *<start\_position\>*, *<regex\_occurrence\>*, or *<regex\_capture\_group\>*.



## Example

The following example returns the day ***01*** from the date value ***20140401***:

```
SELECT SUBSTR_REGEXPR('([[:digit:]]{4})([[:digit:]]{2})([[:digit:]]{2})' IN '20140401' GROUP 3) "substring_regexpr" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

