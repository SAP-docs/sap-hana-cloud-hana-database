<!-- loioa85896b8b0de48089f76b73ae7388740 -->

# RECORD\_COMMIT\_TIMESTAMP Function \(Miscellaneous\)

Returns a COMMIT timestamp for the specified row of the given table.



<a name="loioa85896b8b0de48089f76b73ae7388740__section_ipt_snb_hcb"/>

## Syntax

```
RECORD_COMMIT_TIMESTAMP(<table_name_or_alias>)
```



<a name="loioa85896b8b0de48089f76b73ae7388740__section_dpv_44b_hcb"/>

## Syntax Elements


<dl>
<dt><b>

*<table-name-or-alias\>*

</b></dt>
<dd>

Specifies the name or alias of the table to return the COMMIT timestamps for.



</dd>
</dl>



<a name="loioa85896b8b0de48089f76b73ae7388740__section_kwb_s4b_hcb"/>

## Description

Returns a COMMIT timestamp for the specified row of the given table if the table is tracking COMMIT timestamps for each row. The COMMIT timestamp is based on an internal counter that increases on commit operations and does not contain a date or time. If the table is not tracking COMMIT timestamps, the function returns NULL. The COMMIT timestamp is not a real timestamp, but rather the value of the internal counter, which increases on each commit operation of a transaction.

Depending on the table type, DDL statements such as ALTER TABLE can affect the value returned by the RECORD\_COMMIT\_TIMESTAMP function:

-   For column store tables, the returned value is not affected by DDL operations.

-   For row store tables, the returned value is changed to the COMMIT timestamp of the transaction that performed the DDL operation.




<a name="loioa85896b8b0de48089f76b73ae7388740__section_xss_hpb_hcb"/>

## Example

Execute the following statements to create and populate two tables, AA and BB, where AA records COMMIT timestamps and BB does not.

```
CREATE TABLE AA (A int) RECORD COMMIT TIMESTAMP; 
CREATE TABLE BB (B int); 
INSERT INTO AA VALUES (1); 
INSERT INTO BB VALUES (1); 
COMMIT;
```

Assume the transaction is committed with a COMMIT timestamp of 10. Executing the following statement returns the COMMIT timestamp of the transaction, in this case, 10.

```
SELECT RECORD_COMMIT_TIMESTAMP(AA) FROM AA;
```

Executing a similar statement on table BB returns NULL since the RECORD COMMIT TIMESTAMP option was not set for table BB.

```
SELECT RECORD_COMMIT_TIMESTAMP(BB) FROM BB;
```

