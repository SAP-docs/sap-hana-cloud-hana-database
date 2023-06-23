<!-- loio4496cc5717e847feb7daa41516047df9 -->

# IS\_SQL\_INJECTION\_SAFE Function \(Security\)

Checks a specified SQL identifier for possible SQL injection risks.



## Syntax

```
IS_SQL_INJECTION_SAFE(<value>[, <max_tokens>])
```



## Syntax Elements


<dl>
<dt><b>

*<value\>*

</b></dt>
<dd>

Specifies the string to be checked.

```
<value> ::= <string>
```



</dd><dt><b>

*<max\_tokens\>*

</b></dt>
<dd>

Specifies the maximum number of tokens expected in *<value\>*. The default value is 1.

```
<max_tokens> ::= <integer>
```



</dd>
</dl>



## Description

Use this function to ensure a string contains the specified number of tokens and SQL comments before using it in an SQL statement. A 1 \(safe\) is returned when the actual number of tokens found does not exceed *<max\_tokens\>* and no comments were found; otherwise, a 0 is returned \(not safe\).

For the purposes of counting, SAP HANA interprets whitespaces and the following characters as separators between tokens:

```
 , ( ) [ ] . ; : + - * / % ^ < >  =
```



## Example

The following query returns 0 \(not safe\) because two tokens were found and the default to check for was 1.

```
SELECT IS_SQL_INJECTION_SAFE('tab,le') "safe" FROM DUMMY;
```

The following query returns 0 \(not safe\) because comments are not allowed.

```
SELECT IS_SQL_INJECTION_SAFE('mytab /*', 4) "safe" FROM DUMMY;
```

