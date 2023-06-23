<!-- loioe04d1f42467544a38ac2125f046793ae -->

# CURRENT\_UPDATE\_TRANSACTION Function \(Miscellaneous\)

Returns the unique ID of the current transaction when it is in write mode.



## Syntax

```
CURRENT_UPDATE_TRANSACTION()
```



## Description

Returns the unique ID \(BIGINT\) of the current transaction when it is in write mode. If the current transaction is in read mode, the function returns 0.



## Example

The following example returns the current update transaction id.

```
SELECT CURRENT_UPDATE_TRANSACTION() "current update transaction" FROM DUMMY;
```

