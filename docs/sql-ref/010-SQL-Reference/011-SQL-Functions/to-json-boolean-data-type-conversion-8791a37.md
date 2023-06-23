<!-- loio8791a379ef08455c9bc95f88d4b18630 -->

# TO\_JSON\_BOOLEAN \(Data Type Conversion\)

Converts a given *<value\>* to a boolean value in JSON format, for use with the JSON Document Store feature.



## Syntax

```
TO_JSON_BOOLEAN(<value>)
```



## Description

If the *<value\>* cannot be converted to a JSON boolean value, then an error is returned.



## Example

Create and populate the collection myCollection1:

```
CREATE COLLECTION myCollection1;
INSERT INTO myCollection1 VALUES ('{"k1" : true}');
```

Running the following statement returns an error:

```
SELECT * FROM myCollection1 WHERE "k1" = TRUE;
```

Running the following statement returns the record:

```
SELECT * FROM myCollection1 WHERE "k1" = TO_JSON_BOOLEAN(TRUE);
```

