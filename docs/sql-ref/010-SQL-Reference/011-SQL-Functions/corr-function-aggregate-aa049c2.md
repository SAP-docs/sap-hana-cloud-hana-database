<!-- loioaa049c2602824ba091b1b58153a310e5 -->

# CORR Function \(Aggregate\)

Computes the Pearson product momentum correlation coefficient between two columns. This function can also be used as a window function.



## Syntax

**Aggregate function:**

```
CORR(<column1>, <column2>)
```

**Window function:**

```
CORR(<column1>, <column2>) <window_specification>
```



## Syntax Elements


<dl>
<dt><b>

*<column1\>* and *<column2\>*

</b></dt>
<dd>

Specifies the columns providing the input data for the correlation.

The values of *<column1\>* and *<column2\>* can be of any numeric type.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



## Description

Computes the Pearson product momentum correlation coefficient between two columns.

The result ranges from -1 to 1, depending on the correlation, or NULL if a correlation cannot be computed.

The result can return NULL for one of the following reasons:

-   Less than two value pairs are correlated after NULLs have been removed
-   There is zero variance in at least one of the two columns



## Examples

The examples below assume that a correlation table has been created with the following values:

```
CREATE COLUMN TABLE correlationTable (
    ts_id NVARCHAR(20),
    DATE DAYDATE,
    value1 DOUBLE,
    value2 DOUBLE);

INSERT INTO correlationTable VALUES ('A', '2014-10-01', 1, 1);
INSERT INTO correlationTable VALUES ('A', '2014-10-02', 2, 2);
INSERT INTO correlationTable VALUES ('A', '2014-10-04', 3, 3);
INSERT INTO correlationTable VALUES ('B', '2014-10-07', 1, 3);
INSERT INTO correlationTable VALUES ('B', '2014-10-11', 2, 2);
INSERT INTO correlationTable VALUES ('B', '2014-10-21', 3, 1);
```

1.  The following aggregate function example returns the correlation between the `ts_id` column and the columns `value1` and `value2`.

    ```
    SELECT ts_id, CORR(value1, value2) FROM correlationTable GROUP BY ts_id;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\(VALUE1, VALUE2\)
    
    </th>
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
    
    B
    
    </td>
    <td valign="top">
    
    \-1
    
    </td>
    </tr>
    </table>
    
2.  The following WHERE clause example returns the correlation between the `ts_id` column and the columns `value1` and `value2` only for rows where `ts_id` equals `A`.

    ```
    SELECT ts_id, CORR(value1, value2) FROM correlationTable
        WHERE ts_id='A' GROUP BY ts_id;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\(VALUE1, VALUE2\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    1
    
    </td>
    </tr>
    </table>
    
3.  The example below uses a window function.

    ```
    SELECT ts_id, CORR(value1, value2) OVER (PARTITION BY ts_id) FROM correlationTable;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\(VALUE1, VALUE2\)OVER\(PARTITIONBYTS\_ID\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    1
    
    </td>
    </tr>
    </table>
    
4.  The example below uses a sliding window function.

    ```
    SELECT ts_id, CORR(value1, value2) OVER (PARTITION BY ts_id ORDER BY date)
        FROM correlationTable ORDER BY ts_id;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\(VALUE1, VALUE2\)OVER\(PARTITIONBYTS\_IDORDERBYDATE\)
    
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
    
    0.9999999999999998
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.9999999999999998
    
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
    
    \-0.9999999999999998
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-0.9999999999999998
    
    </td>
    </tr>
    </table>
    
5.  The example below uses a ROWS BETWEEN clause.

    ```
    SELECT ts_id, CORR(value1, value2) OVER (PARTITION BY ts_id ORDER BY date
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) from correlationTable;
    ```

    The results are as follows:


    <table>
    <tr>
    <th valign="top">

    TS\_ID
    
    </th>
    <th valign="top">

    CORR\(VALUE1, VALUE2\)OVER\(PARTITIONBYTS\_IDORDERBYDATEROWS\)
    
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
    
    0.9999999999999998
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    0.9999999999999998
    
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
    
    \-0.9999999999999998
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    B
    
    </td>
    <td valign="top">
    
    \-0.9999999999999998
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[AUTO\_CORR Function \(Aggregate\)](auto-corr-function-aggregate-e279ce4.md "Computes all autocorrelation coefficients for a given input expression and returns an array of values.")

[CORR\_SPEARMAN Function \(Aggregate\)](corr-spearman-function-aggregate-0579a65.md "Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. This function can also be used as a window function.")

[CROSS\_CORR Function \(Aggregate\)](cross-corr-function-aggregate-b2197a4.md "Computes all cross-correlation coefficients between two given expressions.")

