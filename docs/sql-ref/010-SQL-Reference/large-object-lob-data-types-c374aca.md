<!-- loioc374aca91944460b834ef1d5ceb82acf -->

# Large Object \(LOB\) Data Types

LOB \(large objects\) data types, such as NCLOB, and BLOB, are used to store a large amount of data, such as text documents and images.




<dl>
<dt><b>

BLOB

</b></dt>
<dd>

The BLOB data type is used to store large amounts of binary data. BLOB values can be converted to VARBINARY.



</dd><dt><b>

NCLOB and its alias CLOB

</b></dt>
<dd>

The NCLOB data type is used to store a large Unicode character objects. NCLOB values can be converted to NVARCHAR.

In SAP HANA, CLOB is an alias for NCLOB.



</dd>
</dl>

LOB types support the following operations:

-   The LENGTH function for values of type NCLOB/BLOB, which returns the LOB length in bytes.

-   The SUBSTR function for values of type NCLOB, which returns the substring of an NCLOB value.

-   The COALESCE function.

-   The LIKE and CONTAINS predicate for values of type NCLOB.

-   The IS NULL predicate for values of type NCLOB/BLOB.


LOB data types have the following restrictions:

-   LOB columns cannot appear in ORDER BY or GROUP BY clauses.

-   LOB columns cannot appear in FROM clauses as join predicates.

-   LOB columns cannot appear in WHERE clauses as predicates other than LIKE \(meaning that no comparison is allowed\).

-   LOB columns cannot appear in SELECT clauses as aggregate function arguments.

-   LOB columns cannot appear in SELECT DISTINCT clauses.

-   LOB columns cannot be used in set operations such as EXCEPT. UNION ALL is an exception.

-   LOB columns cannot be used as primary keys.

-   LOB columns cannot be used in CREATE INDEX statements.

-   LOB columns cannot be used in statistics update statements.


**Related Information**  


[System Limitations](system-limitations-20a7605.md "Limitations to take into consideration when administering an SAP HANA Cloud database.")

