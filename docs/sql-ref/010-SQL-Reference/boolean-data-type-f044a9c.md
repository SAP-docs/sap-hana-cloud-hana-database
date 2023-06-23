<!-- loiof044a9c7fb7b49159384f92f147345fb -->

# Boolean Data Type

The BOOLEAN data type stores boolean values, which are TRUE, FALSE, and UNKNOWN, where UNKNOWN is a synonym of NULL.



When the client does not support a boolean type, it returns 1 for TRUE and 0 for FALSE.

The following example returns TRUE or 1 for boolean:

```
CREATE ROW TABLE TEST (A BOOLEAN);
INSERT INTO TEST VALUES (TRUE);
INSERT INTO TEST VALUES (FALSE);
INSERT INTO TEST VALUES (UNKNOWN);
INSERT INTO TEST VALUES (NULL);

SELECT A "boolean" FROM TEST WHERE A = TRUE;
```

Although predicates and boolean expressions can both have the same values \(TRUE, FALSE, UNKNOWN\), they are not the same. Therefore, you cannot use boolean type comparisons to compare predicates, or use predicates where boolean expressions should be used.

For example, the following statement does not work:

```
SELECT * FROM DUMMY WHERE ( 'A'>'B' ) = ( 'C'>'D' );
```

The following statement is the correct way to achieve the results desired from the statement above:

```
SELECT * FROM DUMMY WHERE
   CASE WHEN ( 'A'>'B' ) THEN TRUE WHEN NOT ( 'A'>'B' ) THEN FALSE ELSE NULL END=   
   CASE WHEN ( 'C'>'D' ) THEN TRUE WHEN NOT ( 'C'>'D' ) THEN FALSE ELSE NULL END;

```

**Related Information**  


[TO\_BOOLEAN Function \(Data Type Conversion\)](011-SQL-Functions/to-boolean-function-data-type-conversion-258b535.md "Converts a value to a BOOLEAN data type.")

