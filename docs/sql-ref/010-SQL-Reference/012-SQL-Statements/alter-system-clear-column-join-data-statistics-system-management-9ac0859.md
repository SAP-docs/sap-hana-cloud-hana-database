<!-- loio9ac0859babf549c1a05bdfd8c9c68f11 -->

# ALTER SYSTEM CLEAR COLUMN JOIN DATA STATISTICS \(System Management\)

Removes join data statistics from the SAP HANA database cache.



## Syntax

```
ALTER SYSTEM CLEAR COLUMN JOIN DATA STATISTICS
```



## Description

Clears all join data statistics from the system so that the next time a join execution is run join data statistics are recalculated in a deterministic way.



<a name="loio9ac0859babf549c1a05bdfd8c9c68f11__section_svq_2db_chb"/>

## Examples

Retrieve, display, and delete column join data statistics.

```
DROP TABLE A;
CREATE COLUMN TABLE A (aa NVARCHAR(2), ab INT);
DROP TABLE B;
CREATE COLUMN TABLE B (b1 INT, b2 NVARCHAR(1));
INSERT INTO A (aa, ab) VALUES ('AA', 1);
INSERT INTO A (aa, ab) VALUES ('BB', 2);
INSERT INTO B (b1, b2) VALUES (1, 'a');
INSERT INTO B (b1, b2) VALUES (3, 'f');
MERGE DELTA OF A;
MERGE DELTA OF B;
```

Perform a join on tables A and B.

```
SELECT * FROM A INNER JOIN B ON A.ab = B.b1;
```

View the column join data statistics for tables A and B.

```
SELECT COUNT(*) FROM M_JOIN_DATA_STATISTICS WHERE schema_name1 = 'SYSTEM' AND table_name1 IN ('A', 'B');
SELECT * FROM M_JOIN_DATA_STATISTICS;
```

Clear the column join data statistics from the system.

```
ALTER SYSTEM CLEAR COLUMN JOIN DATA STATISTICS;
```

Clear the column join data statistics from table A.

```
ALTER TABLE A CLEAR COLUMN JOIN DATA STATISTICS;
```

