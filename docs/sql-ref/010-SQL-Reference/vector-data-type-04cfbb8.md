<!-- loio04cfbb84101145d283680d28edb1e26e -->

# Vector Data Type

Vector data types store collections of numeric elements. The elements in a vector cannot be NULL. The number of elements in a vector is called vector dimension.




<dl>
<dt><b>

REAL\_VECTOR

</b></dt>
<dd>

The REAL\_VECTOR\(*<n\>*\) data type specifies a vector type with REAL \(IEEE 754 single-precision floating-point\) elements. The optional *<n\>* indicates the vector dimension and is an integer between 1 and 65,000. If the dimension is not specified in DDL or DML statements, any dimension in the valid range can be assigned to the vector instance.

> ### Note:  
> REAL\_VECTOR columns are not supported in row tables.



</dd>
</dl>

**Related Information**  


[REAL_VECTOR Data Type](https://help.sap.com/viewer/c40cab369db246f1a17feea1c031ddc1/2024_1_QRC/en-US/3e563557d6314060ae18a789aff4e400.html "The SAP HANA Cloud database has the built-in vector data type REAL_VECTOR.") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA Database Vector Engine Guide](https://help.sap.com/viewer/c40cab369db246f1a17feea1c031ddc1/2024_1_QRC/en-US/8d2675524f454b248de942da9bc04777.html "This guide provides information about the SAP HANA Cloud vector engine.") :arrow_upper_right:

