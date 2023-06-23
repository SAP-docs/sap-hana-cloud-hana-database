<!-- loiof15c8a4db42b46849c62c4f70d47abd2 -->

# CURRENT\_MVCC\_SNAPSHOT\_TIMESTAMP Function \(Datetime\)

Returns the timestamp of the current MVCC snapshot in SSSS format \(seconds past midnight\).



<a name="loiof15c8a4db42b46849c62c4f70d47abd2__sql_function_current_mvcc_snapshot_timestamp_1sql_function_current_mvcc_snapshot_timestamp_syntax"/>

## Syntax

```
CURRENT_MVCC_SNAPSHOT_TIMESTAMP()
```



<a name="loiof15c8a4db42b46849c62c4f70d47abd2__sql_function_current_mvcc_snapshot_timestamp_1sql_function_current_mvcc_snapshot_timestamp_description"/>

## Description

The CURRENT\_MVCC\_SNAPSHOT\_TIMESTAMP function returns the timestamp of the current MVCC snapshot in SSSS format.



<a name="loiof15c8a4db42b46849c62c4f70d47abd2__sql_function_current_mvcc_snapshot_timestamp_1sql_function_current_mvcc_snapshot_timestamp_examples"/>

## Example

The following example returns the timestamp of the current MVCC snapshot:

```
SELECT CURRENT_MVCC_SNAPSHOT_TIMESTAMP() FROM DUMMY;
```

