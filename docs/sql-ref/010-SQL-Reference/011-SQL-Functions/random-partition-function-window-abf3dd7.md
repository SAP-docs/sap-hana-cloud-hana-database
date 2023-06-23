<!-- loioabf3dd7576464c30a7897a05d1ef8cb2 -->

# RANDOM\_PARTITION Function \(Window\)

Partitions an input set randomly into three disjoint subsets by assigning a set number to each row of the input set.



<a name="loioabf3dd7576464c30a7897a05d1ef8cb2__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
RANDOM_PARTITION(<training_set_size>, <validation_set_size>, <test_set_size>, <seed>) <window_specification>
```



<a name="loioabf3dd7576464c30a7897a05d1ef8cb2__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loioabf3dd7576464c30a7897a05d1ef8cb2__sql_function_abs_1sql_function_abs_description"/>

## Description

The three subsets that RANDOM\_PARTITION partitions the set into are called **training**, **validation**, and **testing**. The union of these three subsets may not be the complete initial dataset.

*<training\_set\_size\>*, *<validation\_set\_size\>*, and *<test\_set\_size\>* can be numeric values that specify the sizes of the training, validation, and testing sets, respectively. When all three values are less than one, the sizes are expressed as fractions of the total input size. When all three values are greater than or equal to one, they represent the actual number of elements in the different partitions. *<seed\>* specifies the seed for the random number generation. When set to zero, the *<seed\>* is initialized with the current time.

The set numbers are defined as follows:


<table>
<tr>
<th valign="top">

Set number



</th>
<th valign="top">

Set



</th>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

The value is not assigned to a set



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

The training set



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

The validation set



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

The test set



</td>
</tr>
</table>

Stratified partitions are supported via the PARTITION BY clause.

To generate reproducible partitions by providing a value for the *<seed\>*, ensure that the input set is ordered in the same way in each call to the function. The *<seed\>* value must be larger than zero to generate reproducible partitions; a value of zero does not create reproducible partitions. Do not use *<seed\>* without the ORDER BY clause. The partitions can be non-deterministic among tie values in the *<window\_order\_by\_expression\>*.



<a name="loioabf3dd7576464c30a7897a05d1ef8cb2__sql_function_abs_1sql_function_abs_examples"/>

## Examples

**Stratified partitions**

The following example creates stratified partitions \(random partitions per station with fractional partition sizes\). Since the partition numbers are randomly assigned to the rows, the result might differ from call to call.

```
CREATE TABLE weather (station INT, ts DATE, temperature FLOAT);
INSERT INTO weather VALUES (1, '2014-01-01', 0);
INSERT INTO weather VALUES (1, '2014-01-02', 3);
INSERT INTO weather VALUES (1, '2014-01-03', 4.5);
INSERT INTO weather VALUES (1, '2014-01-04', 6);
INSERT INTO weather VALUES (1, '2014-01-05', 6.3);
INSERT INTO weather VALUES (1, '2014-01-06', 5.9);
INSERT INTO weather VALUES (2, '2014-01-01', 1);
INSERT INTO weather VALUES (2, '2014-01-02', 3.4);
INSERT INTO weather VALUES (2, '2014-01-03', 5);
INSERT INTO weather VALUES (2, '2014-01-04', 6.7);
INSERT INTO weather VALUES (2, '2014-01-05', 4.6);
INSERT INTO weather VALUES (2, '2014-01-06', 6.9);
				
SELECT *, RANDOM_PARTITION(0.5, 0.2, 0.3, 0) OVER (PARTITION BY station ORDER BY ts) AS part_num FROM weather;
```


<table>
<tr>
<th valign="top">

STATION



</th>
<th valign="top">

TS



</th>
<th valign="top">

TEMPERATURE



</th>
<th valign="top">

PART\_NUM



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

01.01.2014



</td>
<td valign="top">

0.0



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

02.01.2014



</td>
<td valign="top">

3.0



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

03.01.2014



</td>
<td valign="top">

4.5



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

04.01.2014



</td>
<td valign="top">

6.0



</td>
<td valign="top">

3



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

05.01.2014



</td>
<td valign="top">

6.3



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

06.01.2014



</td>
<td valign="top">

5.9



</td>
<td valign="top">

3



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

01.01.2014



</td>
<td valign="top">

1.0



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

02.01.2014



</td>
<td valign="top">

3.4



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

03.01.2014



</td>
<td valign="top">

5.0



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

04.01.2014



</td>
<td valign="top">

6.7



</td>
<td valign="top">

3



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

05.01.2014



</td>
<td valign="top">

4.9



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

06.01.2014



</td>
<td valign="top">

6.9



</td>
<td valign="top">

3



</td>
</tr>
</table>

**Random partitions with explicit partition sizes**

The following example creates random partitions with explicit partition sizes:

```
DROP TABLE weather;
CREATE ROW TABLE weather (station INT, ts DATE, temperature FLOAT);
INSERT INTO weather VALUES(1, '2014-01-01', 0.0);
INSERT INTO weather VALUES(1, '2014-01-02', 3.0);
INSERT INTO weather VALUES(1, '2014-01-03', 4.5);
INSERT INTO weather VALUES(1, '2014-01-04', 6.0);
INSERT INTO weather VALUES(1, '2014-01-05', 6.3);
INSERT INTO weather VALUES(1, '2014-01-06', 5.9);
INSERT INTO weather VALUES(2, '2014-01-01', 1.0);
INSERT INTO weather VALUES(2, '2014-01-02', 3.4);
INSERT INTO weather VALUES(2, '2014-01-03', 5.0);
INSERT INTO weather VALUES(2, '2014-01-04', 6.7);
INSERT INTO weather VALUES(2, '2014-01-05', 4.6);
INSERT INTO weather VALUES(2, '2014-01-06', 6.9);

SELECT *, RANDOM_PARTITION(5, 2, 3, 0) OVER (ORDER BY temperature) AS part_num FROM weather;
```


<table>
<tr>
<th valign="top">

STATION



</th>
<th valign="top">

TS



</th>
<th valign="top">

TEMPERATURE



</th>
<th valign="top">

PART\_NUM



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

01.01.2014



</td>
<td valign="top">

0



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

01.01.2014



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

02.01.2014



</td>
<td valign="top">

3



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

02.01.2014



</td>
<td valign="top">

3.4



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

03.01.2014



</td>
<td valign="top">

4.5



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

05.01.2014



</td>
<td valign="top">

4.6



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

03.01.2014



</td>
<td valign="top">

5



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

06.01.2014



</td>
<td valign="top">

5.9



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

04.01.2014



</td>
<td valign="top">

6



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

05.01.2014



</td>
<td valign="top">

6.3



</td>
<td valign="top">

3



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

04.01.2014



</td>
<td valign="top">

6.7



</td>
<td valign="top">

3



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

06.01.2014



</td>
<td valign="top">

6.9



</td>
<td valign="top">

3



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

