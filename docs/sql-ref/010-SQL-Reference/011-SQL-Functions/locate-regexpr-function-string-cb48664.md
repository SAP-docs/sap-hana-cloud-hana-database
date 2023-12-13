<!-- loiocb4866494bd647cd8926763aa940f613 -->

# LOCATE\_REGEXPR Function \(String\)

Searches a string for a regular expression pattern and returns an integer indicating the beginning position, or the ending position plus 1, of one occurrence of the matched substring.



## Syntax

```
LOCATE_REGEXPR( [ <regex_position_start_or_after> ] <pattern> 
   [  FLAG <flag> ] 
   IN <regex_subject_string> 
   [ FROM <start_position> ] 
   [ OCCURRENCE <regex_occurrence> ] 
   [ GROUP <regex_capture_group> ] 
)
```



## Syntax Elements


<dl>
<dt><b>

*<regex\_position\_start\_or\_after\>*

</b></dt>
<dd>

Searches a string for a regular expression pattern and returns an integer indicating the beginning position, or the ending position plus 1, of one occurrence of the matched substring.

```
<regex_position_start_or_after> ::= START | AFTER 
```

If *<regex\_position\_start\_or\_after\>* is not specified, then START is implicit.



</dd><dt><b>

*<pattern\>*

</b></dt>
<dd>

A search pattern based on Perl Compatible Regular Expression \(PCRE\).



</dd><dt><b>

*<flag\>*

</b></dt>
<dd>

The matching behavior of the function can be defined by the *<flag\>* literal. The following options are available:

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

```
<regex_subject_string> ::= <string>
```

Specifies a string in which to search for the regular expression pattern.



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

The *<start\_position\>* parameter is a positive integer and indicates the character of *<regex\_subject\_string\>* where the search is started. If *<start\_position\>* is not a positive integer, then 0 is returned.

```
<start_position> ::= <positive_integer>
```



</dd><dt><b>

*<regex\_occurrence\>*

</b></dt>
<dd>

Specifies a positive integer to the occurrence of the *<pattern\>* in *<regex\_subject\_string\>*. The default is 1.

```
<regex_occurrence> ::= <integer>
```

If *<regex\_occurrence\>* is not a positive integer, then 0 is returned.



</dd><dt><b>

*<regex\_capture\_group\>*

</b></dt>
<dd>

The *<regex\_capture\_group\>* parameter is a non-negative integer and indicates the number of the captured substring's group by the regular expression. The default is 0.

```
<regex_capture_group> ::= <integer>
```

If *<regex\_capture\_group\>* is a negative integer, then 0 is returned.



</dd>
</dl>



## Description

Searches a string for a regular expression pattern and returns an integer indicating the beginning position, or the ending position plus 1, of one occurrence of the matched substring.

If any of the following parameters is `NULL`: *<pattern\>*, *<flag\>*, *<regex\_subject\_string\>*, , *<start\_position\>*, *<regex\_occurrence\>* or *<regex\_capture\_group\>*, then the function returns NULL.



## Example

This example returns the start position of the day part from the date value 20140401; it returns 7:

```
SELECT LOCATE_REGEXPR(START '([[:digit:]]{4})([[:digit:]]{2})([[:digit:]]{2})' IN '20140401' GROUP 3) "locate_regexpr" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

