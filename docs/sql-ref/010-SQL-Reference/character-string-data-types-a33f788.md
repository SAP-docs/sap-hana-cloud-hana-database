<!-- loioa33f7884b0c14c00b1a76ecd8af5feca -->

# Character String Data Types

Character string data types are used to store values that contain character strings.



In SAP HANA, collation expressions are not supported, and values of string data type are compared using a binary comparison.

The SAP HANA database does not officially support the CHAR and NCHAR datatypes. Even though they are available for use, they are only for legacy support and consistent behavior is not guaranteed for values of these types between a row table and a column table. Use NVARCHAR instead.


<dl>
<dt><b>

NVARCHAR and its alias VARCHAR

</b></dt>
<dd>

The NVARCHAR\(*<n\>*\) data type specifies a variable-length Unicode character set string, where *<n\>* indicates the maximum length in characters and is an integer between 1 and 5000. If the length is not specified in DDL statements, then the default of 1 is used.

If the NVARCHAR\(*<n\>*\) is used in a DML query, for example ***CAST \(A as NVARCHAR\(n\)\)***, then *<n\>* indicates the maximum length of the string in characters. If the length is not specified, then the default of 5000 is used.

In SAP HANA, VARCHAR is an alias for NVARCHAR.



</dd>
</dl>

