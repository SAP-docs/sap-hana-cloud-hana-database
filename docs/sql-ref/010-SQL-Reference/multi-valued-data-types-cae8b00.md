<!-- loiocae8b00a6a964cb8a06d2c00dac4ad05 -->

# Multi-valued Data Types

Multi-valued types are used to store collections of values sharing the same data type.



SAP HANA supports the ARRAY data type, used to store collections of values sharing the same data type where each element is associated with exactly one ordinal position. Arrays can contain NULL values as elements to indicate the absence of a value. Arrays with the WITHOUT DUPLICATES constraint cannot have the same non-NULL value more than once.

Arrays are immutable: adding, removing, or changing elements is not possible. Also, the nesting of arrays inside of array elements is not supported.



## Supported functions and expressions for the ARRAY type

-   *<ARRAY\>* || *<ARRAY\>* \(concatenation\) \(SQLScript\)

-   *<ARRAY\>*\[*<index\>*\] \(element access\) \(SQLScript\)

-   CARDINALITY Function

-   MEMBER\_AT Function

-   \[NOT\] MEMBER OF Function

-   SUBARRAY Function

-   TRIM\_ARRAY Function

-   UNNEST \(SQLScript\)


**Related Information**  


[Array Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/cba8ef91ba944e37beb26eb8bd995c2f.html "") :arrow_upper_right:

[TRIM\_ARRAY Function \(Array\)](011-SQL-Functions/trim-array-function-array-565f8f6.md "Removes the specified number of elements from the end of an array.")

[UNNEST Function](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/4f12887c7941410d802a36c3f1a87a59.html "") :arrow_upper_right:

[SUBARRAY Function \(Array\)](011-SQL-Functions/subarray-function-array-49d7752.md "Returns a subset of values from the specified array beginning from the specified start position.")

[MEMBER\_AT Function \(Array\)](011-SQL-Functions/member-at-function-array-f17a873.md "Returns values from a specified array position.")

[MEMBER OF Predicate](member-of-predicate-f666b95.md "Determines whether a value is a member of an array.")

[CARDINALITY Function \(Array\)](011-SQL-Functions/cardinality-function-array-21c6746.md "Returns the number of elements in a specified array.")

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

