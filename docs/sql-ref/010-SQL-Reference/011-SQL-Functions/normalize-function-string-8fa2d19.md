<!-- loio8fa2d19e3dae4de2a4613a4987858894 -->

# NORMALIZE Function \(String\)

Applies a normalizing format to a character value expression and returns a normalized string.



## Syntax

```
NORMALIZE( <character_value_expression> [ , <normalized_format> ] )
```



<a name="loio8fa2d19e3dae4de2a4613a4987858894__section_plp_ljc_fbb"/>

## Syntax Elements


<dl>
<dt><b>

*<character\_value\_expression\>*

</b></dt>
<dd>

Specifies the NVARCHAR string to normalize.



</dd><dt><b>

*<normalized\_format\>*

</b></dt>
<dd>

Specifies the encoding format to use for the result. The default format is NFC.

```
<normalized_format> ::=
 NFC
 | NFD
 | NFKC
 | NFKD
```



</dd>
</dl>

The four Unicode normalization forms are as follows:


<table>
<tr>
<th valign="top">

Form

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Normalization Form D \(NFD\)

</td>
<td valign="top">

Specifies canonical decomposition.

</td>
</tr>
<tr>
<td valign="top">

Normalization Form C \(NFC\)

</td>
<td valign="top">

Specifies canonical decomposition followed by canonical composition.

</td>
</tr>
<tr>
<td valign="top">

Normalization Form KD \(NFKD\)

</td>
<td valign="top">

Specifies compatibility decomposition.

</td>
</tr>
<tr>
<td valign="top">

Normalization Form KC \(NFKC\)

</td>
<td valign="top">

Specifies compatibility decomposition followed by canonical composition.

</td>
</tr>
</table>



<a name="loio8fa2d19e3dae4de2a4613a4987858894__section_bd1_l3c_fbb"/>

## Description

The Unicode standard defines two formal types, which are canonically and compatibility equivalent to the same characters by four normalization forms. The Unicode normalization algorithm puts all combined marks in a specified order. Decomposition only or decomposition followed by the composition rule is applied to transform each string. The details can be found from the following Unicode Standard Annex \#15: [http://www.unicode.org/reports/tr15/](http://www.unicode.org/reports/tr15/)



<a name="loio8fa2d19e3dae4de2a4613a4987858894__section_ayn_m3c_fbb"/>

## Example

The examples in this section use the NORMALIZE function to return the normalized equivalent of *<character\_value\_expression\>* based on the *<normalized\_format\>* form.

The following is an example of canonical equivalence:


<table>
<tr>
<th valign="top">

Statement

</th>
<th valign="top">

Result

</th>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('Å') FROM DUMMY;
```



</td>
<td valign="top">

Å \(0x00C5\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('A °') FROM DUMMY;
```



</td>
<td valign="top">

Å

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('Å', 'NFC') FROM DUMMY;
```



</td>
<td valign="top">

Å \(0x00C5\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('Å', 'NFD') FROM DUMMY;
```



</td>
<td valign="top">

A °\(0x0041 0x030A\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('A °', 'NFC') FROM DUMMY;
```



</td>
<td valign="top">

Å \(0x00C5\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('A °', 'NFD') FROM DUMMY;
```



</td>
<td valign="top">

A °\(0x0041 0x030A\)

</td>
</tr>
</table>

> ### Note:  
> The example is illustrative and does not work as shown with copy and paste.

The following is an example of compatibility equivalence:


<table>
<tr>
<th valign="top">

Statement

</th>
<th valign="top">

Result

</th>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('ﻉ', 'NFKC') FROM DUMMY;
```



</td>
<td valign="top">

ﻉ \(positional variants\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE ('ﻊ', 'NFKC') FROM DUMMY;
```



</td>
<td valign="top">

ﻉ \(positional variants\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('①', 'NFKC') FROM DUMMY;
```



</td>
<td valign="top">

1 \(circled variants\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('ｶ', 'NFKC') FROM DUMMY;	
```



</td>
<td valign="top">

カ \(width variants\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('¼', 'NFKC') FROM DUMMY;
```



</td>
<td valign="top">

1/4 \(fractions\)

</td>
</tr>
<tr>
<td valign="top">

```
SELECT NORMALIZE('i⁹', 'NFD') FROM DUMMY;
```



</td>
<td valign="top">

i9 \(superscripts/subscripts\)

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

