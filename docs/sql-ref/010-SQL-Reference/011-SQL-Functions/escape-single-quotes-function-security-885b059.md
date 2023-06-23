<!-- loio885b059cc20340979c8927c9301ceb63 -->

# ESCAPE\_SINGLE\_QUOTES Function \(Security\)

Escapes single quotes in the specified string.



## Syntax

```
ESCAPE_SINGLE_QUOTES(<value>)
```



## Description

Escapes single quotes \(apostrophes\) in the given string *<value\>*, ensuring a valid SQL string literal is used in dynamic SQL statements to prevent SQL injections. Returns the input string with escaped single quotes.



## Examples

The following query escapes the parameter content ***Str'ing*** to ***Str''ing***.

```
SELECT ESCAPE_SINGLE_QUOTES('Str''ing') "string_literal" FROM DUMMY;
```

The following query example shows the strings retrieved from a table ***t***, both without and with ESCAPE\_SINGLE\_QUOTES applied. The column `col_txt` contains the two entries `Adam's` and `Eve`.

```
CREATE COLUMN TABLE txt(
col_txt NVARCHAR(5000) NOT NULL);

INSERT INTO txt VALUES ('Adam''s');
INSERT INTO txt VALUES ('Eve');

SELECT col_txt, escape_single_quotes(col_txt) FROM txt;
```

The results are as follows:


<table>
<tr>
<th valign="top">

COL\_TXT



</th>
<th valign="top">

ESCAPE\_SINGLE\_QUOTES\(COL\_TXT\)



</th>
</tr>
<tr>
<td valign="top">

Adam's



</td>
<td valign="top">

Adam''s



</td>
</tr>
<tr>
<td valign="top">

Eve



</td>
<td valign="top">

Eve



</td>
</tr>
</table>

