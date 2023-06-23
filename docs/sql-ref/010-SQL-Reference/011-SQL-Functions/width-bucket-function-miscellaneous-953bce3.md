<!-- loio953bce3cc9a84ebfa77c17ab687ff0ee -->

# WIDTH\_BUCKET Function \(Miscellaneous\)

Returns the bucket number that has been assigned to the result of a specified expression.



<a name="loio953bce3cc9a84ebfa77c17ab687ff0ee__sql_function_width_bucket_1sql_function_width_bucket_syntax"/>

## Syntax

```
WIDTH_BUCKET(<expression>, <min_value>, <max_value>, <num_buckets>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the value that the histogram is created for. *<expression\>* must be a numeric or datetime value, or a value that can be implicitly converted to a numeric or datetime value. If *<expression\>* evaluates to NULL, then *<expression\>* returns NULL.



</dd><dt><b>

*<min\_value\>*

</b></dt>
<dd>

Specifies the minimum endpoint range for *<expression\>*. *<min\_value\>* must be a numeric or datetime value and cannot evaluate to NULL.



</dd><dt><b>

*<max\_value\>*

</b></dt>
<dd>

Specifies the maximum endpoint range for *<expression\>*. *<max\_value\>* must be a numeric or datetime value and cannot evaluate to NULL.



</dd><dt><b>

*<num\_buckets\>*

</b></dt>
<dd>

Specifies the number of buckets to distribute values across. *<num\_buckets\>* must be a positive integer.



</dd>
</dl>



<a name="loio953bce3cc9a84ebfa77c17ab687ff0ee__sql_function_width_bucket_1sql_function_width_bucket_description"/>

## Description

The returned bucket number is an integer between 0 and *<num\_buckets\>* +1. This function always returns *<num\_buckets\>* plus two additional buckets: bucket 0 and *<num\_buckets\>*+1. Bucket 0 contains the count of values less than *<min\_value\>* and bucket *<num\_buckets\>* +1 contains the count of values greater than or equal to *<max\_value\>*.



<a name="loio953bce3cc9a84ebfa77c17ab687ff0ee__sql_function_width_bucket_1sql_function_width_bucket_examples"/>

## Example

The following example returns the bucket numbers for ***myTable***:

```
CREATE TABLE myTable (myValues INT);
INSERT INTO myTable VALUES(1);
INSERT INTO myTable VALUES(2);
INSERT INTO myTable VALUES(3);
INSERT INTO myTable VALUES(4);
INSERT INTO myTable VALUES(5);

SELECT myValues, WIDTH_BUCKET( myValues, 2, 5, 2 ) AS "BucketNo" FROM myTable;
```


<table>
<tr>
<th valign="top">

myValues



</th>
<th valign="top">

BucketNo



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

75



</td>
<td valign="top">

3



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

