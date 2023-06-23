<!-- loio9ae97edbfee241138fcc1c45c079b3e2 -->

# CURRENT\_UPDATE\_STATEMENT\_SEQUENCE Function \(Miscellaneous\)

Returns the number of write statements that have been issued in a transaction incremented by 1.



## Syntax

```
CURRENT_UPDATE_STATEMENT_SEQUENCE()
```



## Description

Returns the number of write statements that have been issued in a transaction incremented by 1. If the transaction has never issued a write transaction, then the function returns 1. The initial value is 1. In a read transaction, the function always returns 1.



## Examples

The following example shows how to retrieve the current write statement sequence number of the current transaction and returns 1:

```
CREATE COLUMN TABLE T(id INT);
INSERT INTO T VALUES (1);
SELECT CURRENT_UPDATE_STATEMENT_SEQUENCE() "statement sequence number" FROM DUMMY;
```

The following statement also returns 1:

```
DELETE FROM T;
SELECT CURRENT_UPDATE_STATEMENT_SEQUENCE() "statement sequence number" FROM DUMMY;
```

