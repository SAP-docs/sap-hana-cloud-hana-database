<!-- loiofcf204141f89497bb07f8efbb1bb92da -->

# DFT Function \(Aggregate\)

Computes expressions and returns an array with specific elements.



## Syntax

```
DFT( <expression>, <N> { <series_orderby> | <order_by_clause> } ).{ REAL | IMAGINARY | AMPLITUDE | PHASE }
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies a value assumed to be a sample taken at a constant time interval. *<expression\>* cannot contain any NULL values.



</dd><dt><b>

*<N\>*

</b></dt>
<dd>

This parameter must be a power of 2. The input is padded with zeros if it contains less than *<N\>* elements.



</dd><dt><b>

*<series\_orderby\>*

</b></dt>
<dd>

The SERIES definition can only be used with an equidistant series.

```
<series_orderby> ::= SERIES( <series_period> <series_equidistant_definition> )
```

The series must not contain missing elements. For more information about this clause, see the SERIES\_GENERATE function.



</dd><dt><b>

*<order\_by\_clause\>*

</b></dt>
<dd>

Specifies the sort order of the input rows.

```
<order_by_clause> ::= ORDER BY <order_by_expression> [, <order_by_expression> [,...] ]

<order_by_expression> ::= 
 <column_name> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 
 | <column_position> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 

<collate_clause> ::= COLLATE <collation_name>
```

*<collate\_clause\>* specifies the collation to use for ordering values in the results. *<collate\_clause\>* can only be used on columns defined as NVARCHAR \(or VARCHAR, which is a synonym for NVARCHAR\).*<collation\_name\>* is one of the supported collation names listed in the COLLATIONS system view.



</dd>
</dl>



## Description

Computes the Discrete Fourier Transform of an expression for the first *<N\>* values and returns an array with exactly *<N\>* elements.

The returned values depend on the output parameter, which must be one of REAL, IMAGINARY, AMPLITUDE, or PHASE.



## Examples

The example below computes the Discrete Fourier Transform of a column in an equidistant series.

```
SELECT DFT(FRACTION_OF_MIN_MAX_RANGE, 4 SERIES(EQUIDISTANT INCREMENT BY 1 PERIOD FOR SERIES(element_number))).REAL
    FROM SERIES_GENERATE_INTEGER(1,0,10);
```

The example below uses the fictional MY\_TABLE and returns an array with 4 numbers representing the real part of the result.

```
SELECT DFT(col, 4 ORDER BY DATE).REAL FROM MY_TABLE;
```

The example below uses the fictional MY\_TABLE and returns an array with 8 numbers representing the imaginary part of the result.

```
SELECT DFT(col, 8 ORDER BY DATE).IMAGINARY FROM MY_TABLE;
```

The example below uses the fictional MY\_TABLE and returns an array with 8 numbers representing the amplitude part \(i.e. SQRT\(REAL^2 + IMAGINARY^2\)\) of the result.

```
SELECT DFT(col, 8 ORDER BY DATE).AMPLITUDE FROM MY_TABLE;
```

The example below uses the fictional MY\_TABLE returns an array with 8 numbers representing the phase part of the result and ranges between -PI and +PI.

```
SELECT DFT(col, 8 ORDER BY DATE).PHASE FROM MY_TABLE;
```

**Related Information**  


[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[COLLATIONS System View](../../020-System-Views-Reference/021-System-Views/collations-system-view-57ff6fd.md "Provides the list of collations that can be specified in an ORDER BY clause.")

[SERIES\_GENERATE Function \(Series Data\)](series-generate-function-series-data-c810103.md "Generates a complete series table based on the specified series definition.")

