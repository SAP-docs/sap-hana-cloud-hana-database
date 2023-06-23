<!-- loio6b977a21b1d64dfca67c4f9d1c47f4e2 -->

# Binary Data Types

Binary types are used to store bytes of binary data.



A value of type binary can be converted to a value of type NVARCHAR if its size is smaller than or equal to 8192. It can therefore be used like a value of type NVARCHAR except during numeric operations.


<dl>
<dt><b>

VARBINARY

</b></dt>
<dd>

The VARBINARY\(*<n\>*\) data type is used to store binary data of a specified maximum length in bytes, where *<n\>* indicates the maximum length and is an integer between 1 and 5000. If the length is not specified, then the default is 1.



</dd>
</dl>

