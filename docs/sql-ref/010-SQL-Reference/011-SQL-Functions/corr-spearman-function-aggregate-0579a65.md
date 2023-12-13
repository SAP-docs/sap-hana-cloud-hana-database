<!-- loio0579a6540e89468998e0ecfaff69acb0 -->

# CORR\_SPEARMAN Function \(Aggregate\)

Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. This function can also be used as a window function.



## Syntax

**Aggregate function:**

```
CORR_SPEARMAN(<column1>, <column2>)
```

**Window function:**

```
CORR_SPEARMAN(<column1>, <column2>) <window_specification>
```



## Syntax Elements


<dl>
<dt><b>

*<column1\>* and *<column2\>*

</b></dt>
<dd>

Specifies the columns providing the input data for the correlation.

The values of *<column1\>* and *<column2\>* can contain number or character types.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



## Description

Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of *<column1\>* and *<column2\>*.

Although this function is grouped with the aggregate functions, its optional OVER clause positions it as a windows function as well.

The result ranges from -1 to 1, depending on the correlation, or NULL if a correlation could not be computed.

The result can return NULL for one of the following reasons:

-   Less than two value pairs are correlated after NULLs have been removed
-   There is zero variance in at least one of the two columns

Whenever a NULL value is found then both the NULL value and the corresponding value of the other input column are ignored.



## Examples

The example below returns ***\-1***.

```
CREATE COLUMN TABLE A (date DAYDATE, val INT);
INSERT INTO A VALUES ('2014-10-01', 100);
INSERT INTO A VALUES ('2014-10-02', 200);
INSERT INTO A VALUES ('2014-10-03', 300);

CREATE COLUMN TABLE B (date DAYDATE, val INT);
INSERT INTO B VALUES ('2014-10-01', 300);
INSERT INTO B VALUES ('2014-10-02', 200);
INSERT INTO B VALUES ('2014-10-03', 100);

SELECT CORR_SPEARMAN(A.val, B.val) "corr" FROM A, B WHERE A.date = B.date;
```

The examples below assume that the correlation table has been created with the following values:

```
CREATE COLUMN TABLE correlationSpearmanTable (
    ts_id NVARCHAR(20),
    date DAYDATE,
    value1 DOUBLE,
    value2 DOUBLE);

INSERT INTO correlationSpearmanTable VALUES ('A', '2014-10-01', 34.345, 45.345);
INSERT INTO correlationSpearmanTable VALUES ('A', '2014-10-02', 27.145, 28.893);
INSERT INTO correlationSpearmanTable VALUES ('A', '2014-10-02', 48.312, 28.865);
INSERT INTO correlationSpearmanTable VALUES ('A', '2014-10-03', 94.213, 58.854);
INSERT INTO correlationSpearmanTable VALUES ('A', '2014-10-03', 16.567, 28.231);
INSERT INTO correlationSpearmanTable VALUES ('A', '2014-10-03', 38.894, 94.378);
INSERT INTO correlationSpearmanTable VALUES ('B', '2014-10-04', 45.643, 76.987);
INSERT INTO correlationSpearmanTable VALUES ('B', '2014-10-04', 53.345, 50.893);
INSERT INTO correlationSpearmanTable VALUES ('B', '2014-10-04', 66.342, 48.342);
INSERT INTO correlationSpearmanTable VALUES ('B', '2014-10-04', 76.432, 37.234);
INSERT INTO correlationSpearmanTable VALUES ('B', '2014-10-05', 88.432, 23.242);
INSERT INTO correlationSpearmanTable VALUES ('B', '2014-10-05', 93.234, 13.132);
```

1.  Execute the aggregate function example below:

    ```
    SELECT ts_id, CORR_spearman(value1, value2) FROM correlationSpearmanTable GROUP BY ts_id;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\_SPEARMAN\(VALUE1,VALUE2\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    </table>
    
2.  Execute the window function below:

    ```
    SELECT ts_id, CORR_spearman(value1, value2) OVER (PARTITION BY ts_id) FROM correlationSpearmanTable;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\_SPEARMAN\(VALUE1,VALUE2\)OVER\(PARTITIONBYTS\_ID\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.542857
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    </table>
    
3.  Execute the sliding window example below:

    ```
    SELECT ts_id, CORR_spearman(value1, value2) OVER (PARTITION BY ts_id ORDER BY date) FROM correlationSpearmanTable ORDER BY ts_id;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\_SPEARMAN\(VALUE1,VALUE2\)OVER\(PARTITIONBYTS\_IDORDERBYDATE\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    ?
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \-0.5
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \-0.5
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    </table>
    
4.  Execute the ROWS BETWEEN example below:

    ```
    SELECT ts_id, CORR_spearman(value1, value2) OVER (PARTITION BY ts_id ORDER BY date
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) from correlationSpearmanTable;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\_SPEARMAN\(VALUE1,VALUE2\)OVER\(PARTITIONBYTS\_IDORDERBYDATEROWS\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    ?
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \-0.5
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.4
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.7
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    ?
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    </table>
    
5.  Execute the group example below:

    ```
    SELECT ts_id, CORR_spearman(value1, value2) OVER (PARTITION BY ts_id ORDER BY date GROUPS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) FROM correlationSpearmanTable;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\_SPEARMAN\(VALUE1,VALUE2\)OVER\(PARTITIONBYTS\_IDORDERBYDATEGROUPS\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    ?
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \-0.5
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \-0.5
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.5428571428571428
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[AUTO\_CORR Function \(Aggregate\)](auto-corr-function-aggregate-e279ce4.md "Computes all autocorrelation coefficients for a given input expression and returns an array of values.")

[CORR Function \(Aggregate\)](corr-function-aggregate-aa049c2.md "Computes the Pearson product momentum correlation coefficient between two columns. This function can also be used as a window function.")

[CROSS\_CORR Function \(Aggregate\)](cross-corr-function-aggregate-b2197a4.md "Computes all cross-correlation coefficients between two given expressions.")

