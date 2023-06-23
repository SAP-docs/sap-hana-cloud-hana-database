<!-- loio20a78d3275191014b41bae7c4a46d835 -->

# SQL Error Codes

Each SAP HANA error has a numeric error code. The M\_ERROR\_CODES system view contains information about the error codes.



To get a complete list of error codes and their descriptions, execute the following query:

```
SELECT * FROM M_ERROR_CODES ORDER BY CODE ASC;
```

The following table lists error codes and their descriptions for the SAP HANA database:


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

WRN\_GENERAL



</td>
<td valign="top">

A general warning.



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

ERR\_GENERAL



</td>
<td valign="top">

A general error.



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

FATAL\_GENERAL



</td>
<td valign="top">

A fatal error.



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

FATAL\_OUT\_OF\_MEMORY



</td>
<td valign="top">

Cannot allocate enough memory.



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

ERR\_INIT



</td>
<td valign="top">

Initialization error.



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

ERR\_DATA



</td>
<td valign="top">

Invalid data.



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

ERR\_FEATURE\_NOT\_SUPPORTED



</td>
<td valign="top">

The feature is not supported.



</td>
</tr>
<tr>
<td valign="top">

8



</td>
<td valign="top">

ERR\_INV\_ARGUMENT



</td>
<td valign="top">

Invalid argument.



</td>
</tr>
<tr>
<td valign="top">

9



</td>
<td valign="top">

ERR\_INDEX\_OUT\_OF\_BOUNDS



</td>
<td valign="top">

The index is out of bounds.



</td>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

ERR\_AUTHENTICATION\_FAILED



</td>
<td valign="top">

Authentication failed.



</td>
</tr>
<tr>
<td valign="top">

11



</td>
<td valign="top">

ERR\_INV\_STATE



</td>
<td valign="top">

Invalid state.



</td>
</tr>
<tr>
<td valign="top">

12



</td>
<td valign="top">

ERR\_FILE\_OPEN\_FAILED



</td>
<td valign="top">

Cannot open the file.



</td>
</tr>
<tr>
<td valign="top">

13



</td>
<td valign="top">

ERR\_FILE\_CREATE\_WRITE\_FAILED



</td>
<td valign="top">

Cannot create/write the file.



</td>
</tr>
<tr>
<td valign="top">

14



</td>
<td valign="top">

ERR\_DISK\_SPACE\_SHORTAGE



</td>
<td valign="top">

Cannot allocate enough disk space.



</td>
</tr>
<tr>
<td valign="top">

15



</td>
<td valign="top">

ERR\_FILE\_NOT\_FOUND



</td>
<td valign="top">

Cannot find file.



</td>
</tr>
<tr>
<td valign="top">

16



</td>
<td valign="top">

ERR\_RETRY\_STATEMENT



</td>
<td valign="top">

Retry the statement.



</td>
</tr>
<tr>
<td valign="top">

17



</td>
<td valign="top">

ERR\_CATA\_VER\_MISMATCH



</td>
<td valign="top">

The metadata schema version is incompatible between the database and the executable file.



</td>
</tr>
<tr>
<td valign="top">

18



</td>
<td valign="top">

ERR\_SERVICE\_SHUTDOWN



</td>
<td valign="top">

The service is shutting down.



</td>
</tr>
<tr>
<td valign="top">

19



</td>
<td valign="top">

ERR\_INV\_LICENSE



</td>
<td valign="top">

Invalid license.



</td>
</tr>
<tr>
<td valign="top">

20



</td>
<td valign="top">

ERR\_CON\_OUTSIDE\_VALIDITY\_PERIOD



</td>
<td valign="top">

The connection attempt was outside of the user's validity period.



</td>
</tr>
<tr>
<td valign="top">

21



</td>
<td valign="top">

ERR\_PERSISTENCE



</td>
<td valign="top">

Persistence error.



</td>
</tr>
<tr>
<td valign="top">

22



</td>
<td valign="top">

ERR\_RECOMPILE\_STATEMENT



</td>
<td valign="top">

A statement recompile is required.



</td>
</tr>
<tr>
<td valign="top">

128



</td>
<td valign="top">

ERR\_TX



</td>
<td valign="top">

Transaction error.



</td>
</tr>
<tr>
<td valign="top">

129



</td>
<td valign="top">

ERR\_TX\_ROLLBACK



</td>
<td valign="top">

The transaction is rolled back by an internal error.



</td>
</tr>
<tr>
<td valign="top">

130



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_INTEGRITY



</td>
<td valign="top">

The transaction rolled back by an integrity constraint violation.



</td>
</tr>
<tr>
<td valign="top">

131



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_LOCK\_TIMEOUT



</td>
<td valign="top">

The transaction is rolled back by a lock wait timeout.



</td>
</tr>
<tr>
<td valign="top">

132



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_RESOURCE



</td>
<td valign="top">

The transaction is rolled back due to unavailable resources.



</td>
</tr>
<tr>
<td valign="top">

133



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_DEADLOCK



</td>
<td valign="top">

The transaction is rolled back by a detected deadlock.



</td>
</tr>
<tr>
<td valign="top">

134



</td>
<td valign="top">

FATAL\_REC\_CHKPT\_FILE\_FAIL



</td>
<td valign="top">

Failure accessing the checkpoint file.



</td>
</tr>
<tr>
<td valign="top">

135



</td>
<td valign="top">

FATAL\_REC\_ANCHOR\_FILE\_FAIL



</td>
<td valign="top">

Failure accessing the anchor file.



</td>
</tr>
<tr>
<td valign="top">

136



</td>
<td valign="top">

FATAL\_REC\_LOG\_FILE\_FAIL



</td>
<td valign="top">

Failure accessing the log file.



</td>
</tr>
<tr>
<td valign="top">

137



</td>
<td valign="top">

FATAL\_REC\_ARCHIVE\_FILE\_FAIL



</td>
<td valign="top">

Failure accessing the archive file.



</td>
</tr>
<tr>
<td valign="top">

138



</td>
<td valign="top">

ERR\_TX\_SERIALIZATION



</td>
<td valign="top">

Transaction serialization failure.



</td>
</tr>
<tr>
<td valign="top">

139



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_QUERY\_CANCEL



</td>
<td valign="top">

The current operation was canceled by request and the transaction was rolled back.



</td>
</tr>
<tr>
<td valign="top">

140



</td>
<td valign="top">

ERR\_TX\_INV\_TID



</td>
<td valign="top">

Invalid write-transaction identifier.



</td>
</tr>
<tr>
<td valign="top">

141



</td>
<td valign="top">

ERR\_INV\_LOG\_FILE\_FAIL



</td>
<td valign="top">

Failure in accessing the invisible log file.



</td>
</tr>
<tr>
<td valign="top">

142



</td>
<td valign="top">

ERR\_TX\_EXCEED\_MAX\_TX\_NUM



</td>
<td valign="top">

Exceeded maximum number of concurrent transactions.



</td>
</tr>
<tr>
<td valign="top">

143



</td>
<td valign="top">

ERR\_TX\_SERIALIZATION\_WITH\_TIMEOUT



</td>
<td valign="top">

There is a transaction serialization failure until the timeout expires.



</td>
</tr>
<tr>
<td valign="top">

144



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_UNIQUE\_VIOLATED



</td>
<td valign="top">

The transaction rollback unique constraint has been violated.



</td>
</tr>
<tr>
<td valign="top">

145



</td>
<td valign="top">

ERR\_TX\_DIST\_FAILURE



</td>
<td valign="top">

The transaction distribution work failed.



</td>
</tr>
<tr>
<td valign="top">

146



</td>
<td valign="top">

ERR\_TX\_LOCK\_ACQUISITION\_FAIL



</td>
<td valign="top">

The resource is busy and NOWAIT has been specified.



</td>
</tr>
<tr>
<td valign="top">

147



</td>
<td valign="top">

ERR\_TX\_DATA\_LOG\_INCONSISTENT



</td>
<td valign="top">

Inconsistency between data and log.



</td>
</tr>
<tr>
<td valign="top">

148



</td>
<td valign="top">

ERR\_TX\_START\_BLOCKED



</td>
<td valign="top">

The transaction start is blocked until the Master\_Restart finishes.



</td>
</tr>
<tr>
<td valign="top">

149



</td>
<td valign="top">

ERR\_TX\_DIST\_2PC\_FAILURE



</td>
<td valign="top">

Distributed transaction commit failure.



</td>
</tr>
<tr>
<td valign="top">

150



</td>
<td valign="top">

ERR\_TX\_SNAPSHOT\_TOO\_OLD



</td>
<td valign="top">

The statement is canceled or the snapshot timestamp is already invalidated.



</td>
</tr>
<tr>
<td valign="top">

151



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_ROW\_STORE\_FULL



</td>
<td valign="top">

The transaction rollback exceeds the maximum size of the persistent row store data space.



</td>
</tr>
<tr>
<td valign="top">

152



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_ROW\_STORE\_FULL\_DBAREQ



</td>
<td valign="top">

The transaction rollback exceeds the maximum size of the persistent row store data space requested by the DBAdmin's action.



</td>
</tr>
<tr>
<td valign="top">

153



</td>
<td valign="top">

ERR\_TX\_SERIALIZATION\_UNLOCK\_REQUIRED



</td>
<td valign="top">

The transaction serialization failure internally used to distinguish serialization failure caused by delete and other versions.



</td>
</tr>
<tr>
<td valign="top">

154



</td>
<td valign="top">

ERR\_TX\_INDEX\_HANDLE\_ACQUISITION\_FAIL



</td>
<td valign="top">

Failure in acquiring the index handle.



</td>
</tr>
<tr>
<td valign="top">

155



</td>
<td valign="top">

ERR\_TX\_ROLLBACK\_DEFERRED\_FK



</td>
<td valign="top">

The transaction rollback deferred an FK constraint violation.



</td>
</tr>
<tr>
<td valign="top">

208



</td>
<td valign="top">

ERR\_TX\_XAER



</td>
<td valign="top">

XA transaction error.



</td>
</tr>
<tr>
<td valign="top">

209



</td>
<td valign="top">

ERR\_TX\_XAER\_ASYNC



</td>
<td valign="top">

Asynchronous operation error.



</td>
</tr>
<tr>
<td valign="top">

210



</td>
<td valign="top">

ERR\_TX\_XAER\_DUPID



</td>
<td valign="top">

Duplicate XID.



</td>
</tr>
<tr>
<td valign="top">

211



</td>
<td valign="top">

ERR\_TX\_XAER\_INVAL



</td>
<td valign="top">

Invalid argument of XA call.



</td>
</tr>
<tr>
<td valign="top">

212



</td>
<td valign="top">

ERR\_TX\_XAER\_NOTA



</td>
<td valign="top">

No valid XID.



</td>
</tr>
<tr>
<td valign="top">

213



</td>
<td valign="top">

ERR\_TX\_XAER\_OUTSIDE



</td>
<td valign="top">

Outside of global transaction.



</td>
</tr>
<tr>
<td valign="top">

214



</td>
<td valign="top">

ERR\_TX\_XAER\_PROTO



</td>
<td valign="top">

Improper XA call sequence.



</td>
</tr>
<tr>
<td valign="top">

215



</td>
<td valign="top">

ERR\_TX\_XAER\_RMERR



</td>
<td valign="top">

Resource manager error.



</td>
</tr>
<tr>
<td valign="top">

216



</td>
<td valign="top">

ERR\_TX\_XAER\_RMFAIL



</td>
<td valign="top">

Resource manager unavailable.



</td>
</tr>
<tr>
<td valign="top">

217



</td>
<td valign="top">

ERR\_TX\_XA\_RBPROTO



</td>
<td valign="top">

A protocol error occurred in the resource manager.



</td>
</tr>
<tr>
<td valign="top">

218



</td>
<td valign="top">

ERR\_TX\_XA\_RBROLLBACK



</td>
<td valign="top">

The reason that the rollback was caused is unspecified.



</td>
</tr>
<tr>
<td valign="top">

256



</td>
<td valign="top">

ERR\_SQL



</td>
<td valign="top">

SQL processing error.



</td>
</tr>
<tr>
<td valign="top">

257



</td>
<td valign="top">

ERR\_SQL\_PARSE



</td>
<td valign="top">

SQL syntax error.



</td>
</tr>
<tr>
<td valign="top">

258



</td>
<td valign="top">

ERR\_SQL\_INSUFF\_PRIV



</td>
<td valign="top">

Insufficient privilege.



</td>
</tr>
<tr>
<td valign="top">

259



</td>
<td valign="top">

ERR\_SQL\_INV\_TABLE



</td>
<td valign="top">

Invalid table name.



</td>
</tr>
<tr>
<td valign="top">

260



</td>
<td valign="top">

ERR\_SQL\_INV\_COLUMN



</td>
<td valign="top">

Invalid column name.



</td>
</tr>
<tr>
<td valign="top">

261



</td>
<td valign="top">

ERR\_SQL\_INV\_INDEX



</td>
<td valign="top">

Invalid index name.



</td>
</tr>
<tr>
<td valign="top">

262



</td>
<td valign="top">

ERR\_SQL\_INV\_QUERY



</td>
<td valign="top">

Invalid query name.



</td>
</tr>
<tr>
<td valign="top">

263



</td>
<td valign="top">

ERR\_SQL\_INV\_ALIAS



</td>
<td valign="top">

Invalid alias name.



</td>
</tr>
<tr>
<td valign="top">

264



</td>
<td valign="top">

ERR\_SQL\_INV\_DATATYPE



</td>
<td valign="top">

Invalid data type.



</td>
</tr>
<tr>
<td valign="top">

265



</td>
<td valign="top">

ERR\_SQL\_MISSING\_EXP



</td>
<td valign="top">

The expression is missing.



</td>
</tr>
<tr>
<td valign="top">

266



</td>
<td valign="top">

ERR\_SQL\_INCNST\_DATATYPE



</td>
<td valign="top">

Inconsistent data type.



</td>
</tr>
<tr>
<td valign="top">

267



</td>
<td valign="top">

ERR\_SQL\_LONG\_LEN\_TYPE



</td>
<td valign="top">

The specified length is too long for its data type.



</td>
</tr>
<tr>
<td valign="top">

268



</td>
<td valign="top">

ERR\_SQL\_AMBG\_COLUMN



</td>
<td valign="top">

The column is ambiguously defined.



</td>
</tr>
<tr>
<td valign="top">

269



</td>
<td valign="top">

ERR\_SQL\_MANY\_VALUES



</td>
<td valign="top">

There are too many values.



</td>
</tr>
<tr>
<td valign="top">

270



</td>
<td valign="top">

ERR\_SQL\_FEW\_VALUES



</td>
<td valign="top">

There are not enough values.



</td>
</tr>
<tr>
<td valign="top">

271



</td>
<td valign="top">

ERR\_SQL\_DPLC\_ALIAS



</td>
<td valign="top">

Duplicate alias.



</td>
</tr>
<tr>
<td valign="top">

272



</td>
<td valign="top">

ERR\_SQL\_DPLC\_COLUMN



</td>
<td valign="top">

Duplicate column name.



</td>
</tr>
<tr>
<td valign="top">

273



</td>
<td valign="top">

ERR\_SQL\_LONG\_CHAR



</td>
<td valign="top">

Not a single character string.



</td>
</tr>
<tr>
<td valign="top">

274



</td>
<td valign="top">

ERR\_SQL\_INS\_LARGE\_VALUE



</td>
<td valign="top">

The inserted value is too large for the column.



</td>
</tr>
<tr>
<td valign="top">

275



</td>
<td valign="top">

ERR\_SQL\_NOT\_FUNCTION



</td>
<td valign="top">

The aggregate function is not allowed.



</td>
</tr>
<tr>
<td valign="top">

276



</td>
<td valign="top">

ERR\_SQL\_NOT\_SINGLE\_GROUP



</td>
<td valign="top">

Aggregation or grouping is missing.



</td>
</tr>
<tr>
<td valign="top">

277



</td>
<td valign="top">

ERR\_SQL\_NOT\_GROUP\_EXP



</td>
<td valign="top">

This is not a GROUP BY expression.



</td>
</tr>
<tr>
<td valign="top">

278



</td>
<td valign="top">

ERR\_SQL\_NESTED\_WO\_GROUP



</td>
<td valign="top">

The nested group function is without GROUP BY.



</td>
</tr>
<tr>
<td valign="top">

279



</td>
<td valign="top">

ERR\_SQL\_TOO\_DEEP\_NESTED



</td>
<td valign="top">

The group function is nested.



</td>
</tr>
<tr>
<td valign="top">

280



</td>
<td valign="top">

ERR\_SQL\_ORDER\_EXCEED\_NUM



</td>
<td valign="top">

The ORDER BY item must be the number of a SELECT list.



</td>
</tr>
<tr>
<td valign="top">

281



</td>
<td valign="top">

ERR\_SQL\_OUTER\_IN\_OR



</td>
<td valign="top">

The outer join is not allowed in the operand OR or IN.



</td>
</tr>
<tr>
<td valign="top">

282



</td>
<td valign="top">

ERR\_SQL\_OUTER\_CROSS\_JOIN



</td>
<td valign="top">

The two tables cannot be outer-joined to each other.



</td>
</tr>
<tr>
<td valign="top">

283



</td>
<td valign="top">

ERR\_SQL\_OUTER\_MORE\_TWO



</td>
<td valign="top">

A table may be outer joined to at most one other table.



</td>
</tr>
<tr>
<td valign="top">

284



</td>
<td valign="top">

ERR\_SQL\_JOIN\_NOT\_MATCH



</td>
<td valign="top">

The join field does not match.



</td>
</tr>
<tr>
<td valign="top">

285



</td>
<td valign="top">

ERR\_SQL\_INV\_JOIN\_PRED



</td>
<td valign="top">

Invalid join condition.



</td>
</tr>
<tr>
<td valign="top">

286



</td>
<td valign="top">

ERR\_SQL\_LONG\_IDENTIFIER



</td>
<td valign="top">

The identifier is too long.



</td>
</tr>
<tr>
<td valign="top">

287



</td>
<td valign="top">

ERR\_SQL\_NOT\_NULL



</td>
<td valign="top">

Cannot insert NULL or update to NULL.



</td>
</tr>
<tr>
<td valign="top">

288



</td>
<td valign="top">

ERR\_SQL\_EXST\_TABLE



</td>
<td valign="top">

Cannot use a duplicate table name.



</td>
</tr>
<tr>
<td valign="top">

289



</td>
<td valign="top">

ERR\_SQL\_EXST\_INDEX



</td>
<td valign="top">

Cannot use a duplicate index name.



</td>
</tr>
<tr>
<td valign="top">

290



</td>
<td valign="top">

ERR\_SQL\_EXST\_QUERY



</td>
<td valign="top">

Cannot use a duplicate query name.



</td>
</tr>
<tr>
<td valign="top">

291



</td>
<td valign="top">

ERR\_SQL\_NOT\_POS\_ARGUMENT



</td>
<td valign="top">

The argument identifier must be positive.



</td>
</tr>
<tr>
<td valign="top">

292



</td>
<td valign="top">

ERR\_SQL\_FEW\_ARGUMENT



</td>
<td valign="top">

There is a wrong number of arguments.



</td>
</tr>
<tr>
<td valign="top">

293



</td>
<td valign="top">

ERR\_SQL\_INV\_ARGUMENT



</td>
<td valign="top">

There is an argument type mismatch.



</td>
</tr>
<tr>
<td valign="top">

294



</td>
<td valign="top">

ERR\_SQL\_MANY\_PRIMARY\_KEY



</td>
<td valign="top">

You cannot have more than one primary key.



</td>
</tr>
<tr>
<td valign="top">

295



</td>
<td valign="top">

ERR\_SQL\_LONG\_MULTIKEY



</td>
<td valign="top">

The multi key length is too long.



</td>
</tr>
<tr>
<td valign="top">

296



</td>
<td valign="top">

ERR\_SQL\_REP\_TABLE\_KEY



</td>
<td valign="top">

The replicated table must have a primary key.



</td>
</tr>
<tr>
<td valign="top">

297



</td>
<td valign="top">

ERR\_SQL\_REP\_UPDATE\_KEY



</td>
<td valign="top">

You cannot update the primary key field in replicated table.



</td>
</tr>
<tr>
<td valign="top">

298



</td>
<td valign="top">

ERR\_SQL\_NOT\_DDL\_STORE



</td>
<td valign="top">

Cannot store DDL.



</td>
</tr>
<tr>
<td valign="top">

299



</td>
<td valign="top">

ERR\_SQL\_NOT\_DROP\_SYSIDX



</td>
<td valign="top">

Cannot drop the index used to enforce a unique/primary key.



</td>
</tr>
<tr>
<td valign="top">

300



</td>
<td valign="top">

ERR\_SQL\_ARG\_OUT\_OF\_RANGE



</td>
<td valign="top">

The argument index is out of range.



</td>
</tr>
<tr>
<td valign="top">

301



</td>
<td valign="top">

ERR\_SQL\_UNIQUE\_VIOLATED



</td>
<td valign="top">

The unique constraint is violated.



</td>
</tr>
<tr>
<td valign="top">

302



</td>
<td valign="top">

ERR\_SQL\_INV\_CHAR\_VAL



</td>
<td valign="top">

Invalid CHAR or VARCHAR value.



</td>
</tr>
<tr>
<td valign="top">

303



</td>
<td valign="top">

ERR\_SQL\_INV\_DATETIME\_VAL



</td>
<td valign="top">

Invalid DATE TIME or TIMESTAMP value.



</td>
</tr>
<tr>
<td valign="top">

304



</td>
<td valign="top">

ERR\_SQL\_DIV\_BY\_ZERO



</td>
<td valign="top">

The division by zero is undefined.



</td>
</tr>
<tr>
<td valign="top">

305



</td>
<td valign="top">

ERR\_SQL\_SINGLE\_ROW



</td>
<td valign="top">

The single-row query returns more than one row.



</td>
</tr>
<tr>
<td valign="top">

306



</td>
<td valign="top">

ERR\_SQL\_INV\_CURSOR



</td>
<td valign="top">

Invalid cursor.



</td>
</tr>
<tr>
<td valign="top">

307



</td>
<td valign="top">

ERR\_SQL\_NUM\_OUT\_OF\_RANGE



</td>
<td valign="top">

The numeric value is out of range.



</td>
</tr>
<tr>
<td valign="top">

308



</td>
<td valign="top">

ERR\_SQL\_EXST\_COLUMN



</td>
<td valign="top">

The column name already exists.



</td>
</tr>
<tr>
<td valign="top">

309



</td>
<td valign="top">

ERR\_SQL\_SUBQ\_TOP\_ORDERBY



</td>
<td valign="top">

The correlated subquery cannot have TOP or ORDER BY.



</td>
</tr>
<tr>
<td valign="top">

310



</td>
<td valign="top">

ERR\_SQL\_IN\_PROC



</td>
<td valign="top">

There is an SQL error in the procedure.



</td>
</tr>
<tr>
<td valign="top">

311



</td>
<td valign="top">

ERR\_SQL\_DROP\_ALL\_COLUMNS



</td>
<td valign="top">

Cannot drop all columns in a table.



</td>
</tr>
<tr>
<td valign="top">

312



</td>
<td valign="top">

ERR\_SQL\_SEQ\_EXHAUST



</td>
<td valign="top">

The sequence is exhausted.



</td>
</tr>
<tr>
<td valign="top">

313



</td>
<td valign="top">

ERR\_SQL\_INV\_SEQ



</td>
<td valign="top">

Invalid sequence.



</td>
</tr>
<tr>
<td valign="top">

314



</td>
<td valign="top">

ERR\_SQL\_OVERFLOW\_NUMERIC



</td>
<td valign="top">

Numeric overflow.



</td>
</tr>
<tr>
<td valign="top">

315



</td>
<td valign="top">

ERR\_SQL\_INV\_SYNONYM



</td>
<td valign="top">

Invalid synonym.



</td>
</tr>
<tr>
<td valign="top">

316



</td>
<td valign="top">

ERR\_SQL\_INV\_NUM\_ARG\_FUNC



</td>
<td valign="top">

Wrong number of arguments in the function invocation.



</td>
</tr>
<tr>
<td valign="top">

317



</td>
<td valign="top">

ERR\_SQL\_NOT\_MATCH\_PLAN\_TABLE



</td>
<td valign="top">

P\_QUERYPLANS does not exist or is not in a valid format.



</td>
</tr>
<tr>
<td valign="top">

318



</td>
<td valign="top">

ERR\_SQL\_DECIMAL\_PRECISION



</td>
<td valign="top">

The decimal precision specifier is out of range.



</td>
</tr>
<tr>
<td valign="top">

319



</td>
<td valign="top">

ERR\_SQL\_DECIMAL\_SCALE



</td>
<td valign="top">

The decimal scale specifier is out of range.



</td>
</tr>
<tr>
<td valign="top">

320



</td>
<td valign="top">

ERR\_SQL\_LOB\_INDEX



</td>
<td valign="top">

Cannot create an index on an expression with a LOB data type.



</td>
</tr>
<tr>
<td valign="top">

321



</td>
<td valign="top">

ERR\_SQL\_INV\_VIEW



</td>
<td valign="top">

Invalid view name.



</td>
</tr>
<tr>
<td valign="top">

322



</td>
<td valign="top">

ERR\_SQL\_EXST\_VIEW



</td>
<td valign="top">

Cannot use duplicate view name.



</td>
</tr>
<tr>
<td valign="top">

323



</td>
<td valign="top">

ERR\_SQL\_REP\_DPLC\_ID



</td>
<td valign="top">

Duplicate replication ID.



</td>
</tr>
<tr>
<td valign="top">

324



</td>
<td valign="top">

ERR\_SQL\_EXST\_SEQ



</td>
<td valign="top">

Cannot use a duplicate sequence name.



</td>
</tr>
<tr>
<td valign="top">

325



</td>
<td valign="top">

ERR\_SQL\_ESC\_SEQ



</td>
<td valign="top">

Invalid escape sequence.



</td>
</tr>
<tr>
<td valign="top">

326



</td>
<td valign="top">

ERR\_SQL\_SEQ\_CURRVAL



</td>
<td valign="top">

The CURRVAL of the given sequence is not yet defined in this session.



</td>
</tr>
<tr>
<td valign="top">

327



</td>
<td valign="top">

ERR\_SQL\_CANNOT\_EXPLAIN



</td>
<td valign="top">

Cannot explain the plan of the given statement.



</td>
</tr>
<tr>
<td valign="top">

328



</td>
<td valign="top">

ERR\_SQL\_INV\_FUNC\_PROC



</td>
<td valign="top">

Invalid function name or procedure.



</td>
</tr>
<tr>
<td valign="top">

329



</td>
<td valign="top">

ERR\_SQL\_EXST\_FUNC\_PROC



</td>
<td valign="top">

Cannot use duplicate function or procedure names.



</td>
</tr>
<tr>
<td valign="top">

330



</td>
<td valign="top">

ERR\_SQL\_EXST\_SYNONYM



</td>
<td valign="top">

Cannot use duplicate synonym names.



</td>
</tr>
<tr>
<td valign="top">

331



</td>
<td valign="top">

ERR\_SQL\_EXST\_USER



</td>
<td valign="top">

The user name already exists.



</td>
</tr>
<tr>
<td valign="top">

332



</td>
<td valign="top">

ERR\_SQL\_INV\_USER



</td>
<td valign="top">

Invalid user name.



</td>
</tr>
<tr>
<td valign="top">

333



</td>
<td valign="top">

ERR\_SQL\_COLUMN\_NOT\_ALLOWED\_HERE



</td>
<td valign="top">

The column is not allowed.



</td>
</tr>
<tr>
<td valign="top">

334



</td>
<td valign="top">

ERR\_SQL\_INV\_PRIV



</td>
<td valign="top">

Invalid user privilege.



</td>
</tr>
<tr>
<td valign="top">

335



</td>
<td valign="top">

ERR\_SQL\_EXST\_ALIAS



</td>
<td valign="top">

The field alias name already exists.



</td>
</tr>
<tr>
<td valign="top">

336



</td>
<td valign="top">

ERR\_SQL\_INV\_DEFAULT



</td>
<td valign="top">

Invalid default value.



</td>
</tr>
<tr>
<td valign="top">

337



</td>
<td valign="top">

ERR\_SQL\_INTO\_NOT\_ALLOWED



</td>
<td valign="top">

The INTO clause is not allowed for this SELECT statement.



</td>
</tr>
<tr>
<td valign="top">

338



</td>
<td valign="top">

ERR\_SQL\_ZERO\_LEN\_NOT\_ALLOWED



</td>
<td valign="top">

Zero length columns are not allowed.



</td>
</tr>
<tr>
<td valign="top">

339



</td>
<td valign="top">

ERR\_SQL\_INV\_NUMBER



</td>
<td valign="top">

Invalid number.



</td>
</tr>
<tr>
<td valign="top">

340



</td>
<td valign="top">

ERR\_SQL\_VAR\_NOT\_BOUND



</td>
<td valign="top">

Not all variables are bound.



</td>
</tr>
<tr>
<td valign="top">

341



</td>
<td valign="top">

ERR\_SQL\_UNDERFLOW\_NUMERIC



</td>
<td valign="top">

Numeric underflow.



</td>
</tr>
<tr>
<td valign="top">

342



</td>
<td valign="top">

ERR\_SQL\_COLLATE\_CONFLICT



</td>
<td valign="top">

Collation conflict.



</td>
</tr>
<tr>
<td valign="top">

343



</td>
<td valign="top">

ERR\_SQL\_INV\_COLLATE\_NAME



</td>
<td valign="top">

Invalid collate name.



</td>
</tr>
<tr>
<td valign="top">

344



</td>
<td valign="top">

ERR\_SQL\_LOADER\_PARSE



</td>
<td valign="top">

There is a parse error in the data loader.



</td>
</tr>
<tr>
<td valign="top">

345



</td>
<td valign="top">

ERR\_SQL\_NOT\_REP\_TABLE



</td>
<td valign="top">

This is not a replication table.



</td>
</tr>
<tr>
<td valign="top">

346



</td>
<td valign="top">

ERR\_SQL\_INV\_REP\_ID



</td>
<td valign="top">

Invalid replication ID.



</td>
</tr>
<tr>
<td valign="top">

347



</td>
<td valign="top">

ERR\_SQL\_INV\_OPTION



</td>
<td valign="top">

Invalid option in the monitor.



</td>
</tr>
<tr>
<td valign="top">

348



</td>
<td valign="top">

ERR\_SQL\_INV\_DATETIME\_FORMAT



</td>
<td valign="top">

Invalid datetime format.



</td>
</tr>
<tr>
<td valign="top">

349



</td>
<td valign="top">

ERR\_SQL\_CREATE\_UNIQUE\_INDEX



</td>
<td valign="top">

Cannot CREATE UNIQUE INDEX because a duplicate key has been found.



</td>
</tr>
<tr>
<td valign="top">

350



</td>
<td valign="top">

ERR\_SQL\_DROP\_COL\_PRIMARY\_KEY



</td>
<td valign="top">

Cannot drop columns in the primary key column list.



</td>
</tr>
<tr>
<td valign="top">

351



</td>
<td valign="top">

ERR\_SQL\_DROP\_MULTI\_COL\_UNIQUE



</td>
<td valign="top">

This column is referenced in a multi-column constraint.



</td>
</tr>
<tr>
<td valign="top">

352



</td>
<td valign="top">

ERR\_SQL\_CREATE\_UNIQUE\_INDEX\_ON\_CDX\_TAB



</td>
<td valign="top">

Cannot create a unique index on a CDX table.



</td>
</tr>
<tr>
<td valign="top">

353



</td>
<td valign="top">

ERR\_SQL\_EXST\_UPDATE\_LOG\_GROUP



</td>
<td valign="top">

The updated log group name already exists.



</td>
</tr>
<tr>
<td valign="top">

354



</td>
<td valign="top">

ERR\_SQL\_INV\_UPDATE\_LOG\_GROUP\_NAME



</td>
<td valign="top">

Invalid update log group name.



</td>
</tr>
<tr>
<td valign="top">

355



</td>
<td valign="top">

ERR\_SQL\_UPDATE\_LOG\_TABLE\_KEY



</td>
<td valign="top">

The base table of the update log table must have a primary key.



</td>
</tr>
<tr>
<td valign="top">

356



</td>
<td valign="top">

ERR\_SQL\_MAX\_UPDATE\_LOG\_GROUP



</td>
<td valign="top">

You have exceeded the maximum number of update log groups.



</td>
</tr>
<tr>
<td valign="top">

357



</td>
<td valign="top">

ERR\_SQL\_BASE\_TABLE\_ALREADY\_HAS\_ULT



</td>
<td valign="top">

The base table already has an update log table.



</td>
</tr>
<tr>
<td valign="top">

358



</td>
<td valign="top">

ERR\_SQL\_ULT\_CAN\_NOT\_HAVE\_ULT



</td>
<td valign="top">

The update log table cannot have an update log table.



</td>
</tr>
<tr>
<td valign="top">

359



</td>
<td valign="top">

ERR\_SQL\_STR\_LENGTH\_TOO\_LARGE



</td>
<td valign="top">

The string is too long.



</td>
</tr>
<tr>
<td valign="top">

360



</td>
<td valign="top">

ERR\_SQL\_VIEW\_CHECK\_VIOLATION



</td>
<td valign="top">

The view WITH CHECK OPTION where-clause has a violation.



</td>
</tr>
<tr>
<td valign="top">

361



</td>
<td valign="top">

ERR\_SQL\_VIEW\_UPDATE\_VIOLATION



</td>
<td valign="top">

The data manipulation operation is not legal on this view.



</td>
</tr>
<tr>
<td valign="top">

362



</td>
<td valign="top">

ERR\_SQL\_INV\_SCHEMA



</td>
<td valign="top">

Invalid schema name.



</td>
</tr>
<tr>
<td valign="top">

363



</td>
<td valign="top">

ERR\_SQL\_MAX\_NUM\_INDEX\_COLUMN



</td>
<td valign="top">

The number of index columns exceeds the maximum.



</td>
</tr>
<tr>
<td valign="top">

364



</td>
<td valign="top">

ERR\_SQL\_INV\_PARTIAL\_KEY\_SIZE



</td>
<td valign="top">

Invalid partial key size.



</td>
</tr>
<tr>
<td valign="top">

365



</td>
<td valign="top">

ERR\_SQL\_NO\_MATCHING\_UNIQUE\_OR\_PRIMARY\_KEY



</td>
<td valign="top">

There is no matching primary key for this column list.



</td>
</tr>
<tr>
<td valign="top">

366



</td>
<td valign="top">

ERR\_SQL\_NO\_PRIMARY\_KEY



</td>
<td valign="top">

The referenced table does not have a primary key.



</td>
</tr>
<tr>
<td valign="top">

367



</td>
<td valign="top">

ERR\_SQL\_MISMATCH\_OF\_COLUMN\_NUMBERS



</td>
<td valign="top">

The number of referencing columns must match referenced columns.



</td>
</tr>
<tr>
<td valign="top">

368



</td>
<td valign="top">

ERR\_SQL\_TEMP\_TABLE\_WITH\_UNIQUE



</td>
<td valign="top">

The unique constraint is not allowed on the temporary table.



</td>
</tr>
<tr>
<td valign="top">

369



</td>
<td valign="top">

ERR\_SQL\_MAX\_VIEW\_DEPTH



</td>
<td valign="top">

You have exceeded the maximum view depth limit.



</td>
</tr>
<tr>
<td valign="top">

370



</td>
<td valign="top">

ERR\_SQL\_DIRECT\_INSERT\_WITH\_UNIQUE\_INDEX



</td>
<td valign="top">

You cannot perform a DIRECT INSERT operation on a table with unique indexes.



</td>
</tr>
<tr>
<td valign="top">

371



</td>
<td valign="top">

ERR\_SQL\_XML\_PARSE



</td>
<td valign="top">

Invalid XML document.



</td>
</tr>
<tr>
<td valign="top">

372



</td>
<td valign="top">

ERR\_SQL\_XPATH\_PARSE



</td>
<td valign="top">

Invalid XPATH.



</td>
</tr>
<tr>
<td valign="top">

373



</td>
<td valign="top">

ERR\_SQL\_INV\_XML\_DURATION



</td>
<td valign="top">

Invalid XML duration value.



</td>
</tr>
<tr>
<td valign="top">

374



</td>
<td valign="top">

ERR\_SQL\_INV\_XML\_FUNCTION



</td>
<td valign="top">

Invalid XML function usage.



</td>
</tr>
<tr>
<td valign="top">

375



</td>
<td valign="top">

ERR\_SQL\_INV\_XML\_INDEX\_OPERATION



</td>
<td valign="top">

Invalid XML index operation.



</td>
</tr>
<tr>
<td valign="top">

376



</td>
<td valign="top">

ERR\_SQL\_PYTHON



</td>
<td valign="top">

Python built-in procedure error.



</td>
</tr>
<tr>
<td valign="top">

377



</td>
<td valign="top">

ERR\_SQL\_JIT



</td>
<td valign="top">

JIT operation error.



</td>
</tr>
<tr>
<td valign="top">

378



</td>
<td valign="top">

ERR\_SQL\_INV\_COLUMN\_VIEW



</td>
<td valign="top">

Invalid column view.



</td>
</tr>
<tr>
<td valign="top">

379



</td>
<td valign="top">

ERR\_SQL\_TABLE\_SCHEMA\_MISMATCH



</td>
<td valign="top">

Table schema mismatch.



</td>
</tr>
<tr>
<td valign="top">

380



</td>
<td valign="top">

ERR\_SQL\_RUN\_LEVEL\_CHANGE



</td>
<td valign="top">

Failed to change run level.



</td>
</tr>
<tr>
<td valign="top">

381



</td>
<td valign="top">

ERR\_SQL\_RESTART



</td>
<td valign="top">

Failed to restart.



</td>
</tr>
<tr>
<td valign="top">

382



</td>
<td valign="top">

ERR\_SQL\_COLLECT\_ALL\_VERSIONS



</td>
<td valign="top">

Failed to collect all versions of the garbage.



</td>
</tr>
<tr>
<td valign="top">

383



</td>
<td valign="top">

ERR\_SQL\_INV\_IDENTIFIER



</td>
<td valign="top">

Invalid identifier.



</td>
</tr>
<tr>
<td valign="top">

384



</td>
<td valign="top">

ERR\_SQL\_TOO\_LONG\_CONSTANT



</td>
<td valign="top">

The string is too long.



</td>
</tr>
<tr>
<td valign="top">

385



</td>
<td valign="top">

ERR\_SQL\_RESTORE\_SESSION



</td>
<td valign="top">

Could not restore the session.



</td>
</tr>
<tr>
<td valign="top">

386



</td>
<td valign="top">

ERR\_SQL\_EXST\_SCHEMA



</td>
<td valign="top">

Cannot use a duplicate schema name.



</td>
</tr>
<tr>
<td valign="top">

387



</td>
<td valign="top">

ERR\_SQL\_AMBG\_TABLE



</td>
<td valign="top">

The table is ambiguously defined.



</td>
</tr>
<tr>
<td valign="top">

388



</td>
<td valign="top">

ERR\_SQL\_EXST\_ROLE



</td>
<td valign="top">

The role already exists.



</td>
</tr>
<tr>
<td valign="top">

389



</td>
<td valign="top">

ERR\_SQL\_INV\_ROLE



</td>
<td valign="top">

Invalid role name.



</td>
</tr>
<tr>
<td valign="top">

390



</td>
<td valign="top">

ERR\_SQL\_INV\_USERTYPE



</td>
<td valign="top">

Invalid user type.



</td>
</tr>
<tr>
<td valign="top">

391



</td>
<td valign="top">

ERR\_SQL\_INV\_USABLE\_VIEW



</td>
<td valign="top">

Invalidated view.



</td>
</tr>
<tr>
<td valign="top">

392



</td>
<td valign="top">

ERR\_SQL\_CYCLIC\_ROLES



</td>
<td valign="top">

Cannot assign a cyclic role.



</td>
</tr>
<tr>
<td valign="top">

393



</td>
<td valign="top">

ERR\_SQL\_NO\_GRANT\_OPTION\_FOR\_ROLE



</td>
<td valign="top">

The roles must not receive a privilege with a GRANT option.



</td>
</tr>
<tr>
<td valign="top">

394



</td>
<td valign="top">

ERR\_SQL\_CANT\_REVOKE\_ROLE



</td>
<td valign="top">

There was an error revoking the role.



</td>
</tr>
<tr>
<td valign="top">

395



</td>
<td valign="top">

ERR\_SQL\_INV\_USER\_DEFINED\_TYPE



</td>
<td valign="top">

Invalid user-defined type name.



</td>
</tr>
<tr>
<td valign="top">

396



</td>
<td valign="top">

ERR\_SQL\_EXST\_USER\_DEFINED\_TYPE



</td>
<td valign="top">

Cannot use duplicate user-defined type names.



</td>
</tr>
<tr>
<td valign="top">

397



</td>
<td valign="top">

ERR\_SQL\_INV\_OBJ\_NAME



</td>
<td valign="top">

Invalid object name.



</td>
</tr>
<tr>
<td valign="top">

398



</td>
<td valign="top">

ERR\_SQL\_MANY\_ORDER\_BY



</td>
<td valign="top">

Cannot have more than one order by.



</td>
</tr>
<tr>
<td valign="top">

399



</td>
<td valign="top">

ERR\_SQL\_TOO\_DEEP\_ROLE\_TREE



</td>
<td valign="top">

The role tree is too deep.



</td>
</tr>
<tr>
<td valign="top">

400



</td>
<td valign="top">

ERR\_SQL\_INSERT\_ONLY\_TABLE\_WITH\_PRIMARY\_KEY



</td>
<td valign="top">

The primary key is not allowed on an insert-only table.



</td>
</tr>
<tr>
<td valign="top">

401



</td>
<td valign="top">

ERR\_SQL\_INSERT\_ONLY\_TABLE\_WITH\_UNIQUE



</td>
<td valign="top">

The unique constraint is not allowed on an insert-only table.



</td>
</tr>
<tr>
<td valign="top">

402



</td>
<td valign="top">

ERR\_SQL\_DROPPED\_USER



</td>
<td valign="top">

The user was already dropped before the query execution.



</td>
</tr>
<tr>
<td valign="top">

403



</td>
<td valign="top">

ERR\_SQL\_INTERNAL\_ERROR



</td>
<td valign="top">

Internal error.



</td>
</tr>
<tr>
<td valign="top">

404



</td>
<td valign="top">

ERR\_SQL\_INV\_STRUCTURED\_PRIVILEGE\_NAME



</td>
<td valign="top">

Invalid \(non-existent\) structured privilege name.



</td>
</tr>
<tr>
<td valign="top">

405



</td>
<td valign="top">

ERR\_SQL\_DUP\_STRUCTURED\_PRIVILEGE\_NAME



</td>
<td valign="top">

Cannot use duplicate structured privilege name.



</td>
</tr>
<tr>
<td valign="top">

406



</td>
<td valign="top">

ERR\_SQL\_CANT\_UPDATE\_GEN\_COL



</td>
<td valign="top">

INSERT UPDATE and UPSERT are not allowed on the generated field.



</td>
</tr>
<tr>
<td valign="top">

407



</td>
<td valign="top">

ERR\_SQL\_INV\_DATE\_FORMAT



</td>
<td valign="top">

Invalid date format.



</td>
</tr>
<tr>
<td valign="top">

408



</td>
<td valign="top">

ERR\_SQL\_PASS\_OR\_PARAMETER\_NEEDED



</td>
<td valign="top">

A password or parameter is required for the user.



</td>
</tr>
<tr>
<td valign="top">

409



</td>
<td valign="top">

ERR\_SQL\_TOO\_MANY\_PARAMETER\_VALUES



</td>
<td valign="top">

Multiple values for a parameter not supported.



</td>
</tr>
<tr>
<td valign="top">

410



</td>
<td valign="top">

ERR\_SQL\_INV\_PRIVILEGE\_NAMESPACE



</td>
<td valign="top">

Invalid privilege namespace.



</td>
</tr>
<tr>
<td valign="top">

411



</td>
<td valign="top">

ERR\_SQL\_INV\_TABLE\_TYPE



</td>
<td valign="top">

Invalid table type.



</td>
</tr>
<tr>
<td valign="top">

412



</td>
<td valign="top">

ERR\_SQL\_INV\_PASSWORD\_LAYOUT



</td>
<td valign="top">

Invalid password layout.



</td>
</tr>
<tr>
<td valign="top">

413



</td>
<td valign="top">

ERR\_SQL\_PASSWORD\_REUSED



</td>
<td valign="top">

The last password cannot be reused.



</td>
</tr>
<tr>
<td valign="top">

414



</td>
<td valign="top">

ERR\_SQL\_ALTER\_PASSWORD\_NEEDED



</td>
<td valign="top">

The user is forced to change the password.



</td>
</tr>
<tr>
<td valign="top">

415



</td>
<td valign="top">

ERR\_SQL\_USER\_DEACTIVATED



</td>
<td valign="top">

The user is deactivated.



</td>
</tr>
<tr>
<td valign="top">

416



</td>
<td valign="top">

ERR\_SQL\_USER\_LOCKED



</td>
<td valign="top">

The user is locked, try again later.



</td>
</tr>
<tr>
<td valign="top">

417



</td>
<td valign="top">

ERR\_SQL\_CANT\_DROP\_WITHOUT\_CASCADE



</td>
<td valign="top">

Cannot drop without the CASCADE specification.



</td>
</tr>
<tr>
<td valign="top">

418



</td>
<td valign="top">

ERR\_SQL\_INV\_VIEW\_QUERY



</td>
<td valign="top">

Invalid view query for creation.



</td>
</tr>
<tr>
<td valign="top">

419



</td>
<td valign="top">

ERR\_SQL\_CANT\_DROP\_WITH\_RESTRICT



</td>
<td valign="top">

Cannot drop with the RESTRICT specification.



</td>
</tr>
<tr>
<td valign="top">

420



</td>
<td valign="top">

ERR\_SQL\_ALTER\_PASSWORD\_NOT\_ALLOWED



</td>
<td valign="top">

The password change is not currently allowed.



</td>
</tr>
<tr>
<td valign="top">

422



</td>
<td valign="top">

ERR\_SQL\_MIXED\_PRIVILEGE\_NAMESPACES



</td>
<td valign="top">

The privileges must be either all SQL or all from one namespace.



</td>
</tr>
<tr>
<td valign="top">

423



</td>
<td valign="top">

ERR\_SQL\_LVC



</td>
<td valign="top">

AFL error.



</td>
</tr>
<tr>
<td valign="top">

424



</td>
<td valign="top">

ERR\_SQL\_INV\_PACKAGE



</td>
<td valign="top">

Invalid package name.



</td>
</tr>
<tr>
<td valign="top">

425



</td>
<td valign="top">

ERR\_SQL\_EXST\_PACKAGE



</td>
<td valign="top">

Duplicate package name.



</td>
</tr>
<tr>
<td valign="top">

426



</td>
<td valign="top">

ERR\_SQL\_NUM\_COLUMN\_MISMATCH



</td>
<td valign="top">

The number of columns do not match.



</td>
</tr>
<tr>
<td valign="top">

427



</td>
<td valign="top">

ERR\_SQL\_CANT\_RESERVE\_INDEX\_ID



</td>
<td valign="top">

Cannot reserve the index ID anymore.



</td>
</tr>
<tr>
<td valign="top">

428



</td>
<td valign="top">

ERR\_INV\_QUERY\_PLAN\_ID



</td>
<td valign="top">

Invalid query plan ID.



</td>
</tr>
<tr>
<td valign="top">

429



</td>
<td valign="top">

ERR\_SQL\_INTEGRITY\_CHECK\_FAILED



</td>
<td valign="top">

The integrity check failed.



</td>
</tr>
<tr>
<td valign="top">

430



</td>
<td valign="top">

ERR\_SQL\_INV\_USABLE\_PROC



</td>
<td valign="top">

Invalidated procedure.



</td>
</tr>
<tr>
<td valign="top">

431



</td>
<td valign="top">

WRN\_SQL\_NEARLY\_EXPIRED\_PASSWORD



</td>
<td valign="top">

The user's password will expire within few days.



</td>
</tr>
<tr>
<td valign="top">

432



</td>
<td valign="top">

WRN\_SQL\_DEPRECATED\_SYNTAX



</td>
<td valign="top">

This syntax has been deprecated and will be removed in next release.



</td>
</tr>
<tr>
<td valign="top">

433



</td>
<td valign="top">

ERR\_SQL\_NOT\_NULL\_CONSTRAINT



</td>
<td valign="top">

NULL value found.



</td>
</tr>
<tr>
<td valign="top">

434



</td>
<td valign="top">

ERR\_SQL\_INV\_OBJECT



</td>
<td valign="top">

Invalid object ID.



</td>
</tr>
<tr>
<td valign="top">

435



</td>
<td valign="top">

ERR\_SQL\_INV\_EXP



</td>
<td valign="top">

Invalid expression.



</td>
</tr>
<tr>
<td valign="top">

436



</td>
<td valign="top">

ERR\_SQL\_SET\_SYSTEM\_LICENSE



</td>
<td valign="top">

Could not set system license.



</td>
</tr>
<tr>
<td valign="top">

437



</td>
<td valign="top">

ERR\_SQL\_ONLY\_LICENSE\_HANDLING



</td>
<td valign="top">

Only commands for license handling are allowed in current state.



</td>
</tr>
<tr>
<td valign="top">

438



</td>
<td valign="top">

ERR\_SQL\_INVALID\_USER\_PARAMETER\_VALUE



</td>
<td valign="top">

Invalid user parameter value.



</td>
</tr>
<tr>
<td valign="top">

439



</td>
<td valign="top">

ERR\_SQL\_COMPOSITE\_ERROR



</td>
<td valign="top">

Composite error.



</td>
</tr>
<tr>
<td valign="top">

440



</td>
<td valign="top">

ERR\_SQL\_TABLE\_TYPE\_CONVERSION\_ERROR



</td>
<td valign="top">

Table type conversion error.



</td>
</tr>
<tr>
<td valign="top">

441



</td>
<td valign="top">

WRN\_SQL\_DEPRECATED\_FEATURE



</td>
<td valign="top">

This feature has been deprecated and will be removed in next release.



</td>
</tr>
<tr>
<td valign="top">

442



</td>
<td valign="top">

ERR\_SQL\_MAX\_NUM\_COLUMN



</td>
<td valign="top">

The number of columns exceeds its maximum.



</td>
</tr>
<tr>
<td valign="top">

443



</td>
<td valign="top">

ERR\_SQL\_INV\_CALC\_SCENARIO



</td>
<td valign="top">

Invalid calculation scenario name.



</td>
</tr>
<tr>
<td valign="top">

444



</td>
<td valign="top">

ERR\_SQL\_PACKMAN



</td>
<td valign="top">

Package manager error.



</td>
</tr>
<tr>
<td valign="top">

445



</td>
<td valign="top">

ERR\_SQL\_INV\_TRIGGER



</td>
<td valign="top">

Invalid trigger name.



</td>
</tr>
<tr>
<td valign="top">

446



</td>
<td valign="top">

ERR\_SQL\_EXST\_TRIGGER



</td>
<td valign="top">

Cannot use a duplicate trigger name.



</td>
</tr>
<tr>
<td valign="top">

447



</td>
<td valign="top">

ERR\_SQL\_BACKUP\_FAILED



</td>
<td valign="top">

The backup could not be completed.



</td>
</tr>
<tr>
<td valign="top">

448



</td>
<td valign="top">

ERR\_SQL\_RECOVERY\_FAILED



</td>
<td valign="top">

The recovery could not be completed.



</td>
</tr>
<tr>
<td valign="top">

449



</td>
<td valign="top">

ERR\_SQL\_RECOVERY\_STRATEGY



</td>
<td valign="top">

The recovery strategy could not be determined.



</td>
</tr>
<tr>
<td valign="top">

450



</td>
<td valign="top">

ERR\_SQL\_UNSET\_SYSTEM\_LICENSE



</td>
<td valign="top">

Failed to unset the system license.



</td>
</tr>
<tr>
<td valign="top">

451



</td>
<td valign="top">

ERR\_SQL\_NOT\_ALLOWED\_SUBJ\_TAB\_ACCESS\_TRIGGER



</td>
<td valign="top">

The modification of the subject table in the trigger is not allowed.



</td>
</tr>
<tr>
<td valign="top">

452



</td>
<td valign="top">

ERR\_SQL\_INV\_BACKUPID



</td>
<td valign="top">

Invalid backup ID.



</td>
</tr>
<tr>
<td valign="top">

453



</td>
<td valign="top">

ERR\_SQL\_USER\_WITHOUT\_PASSWORD



</td>
<td valign="top">

The user does not have a password.



</td>
</tr>
<tr>
<td valign="top">

454



</td>
<td valign="top">

WRN\_SQL\_WRONG\_HINT\_SYNTAX



</td>
<td valign="top">

Wrong hint syntax.



</td>
</tr>
<tr>
<td valign="top">

455



</td>
<td valign="top">

ERR\_SQL\_READ\_ONLY\_SESSION\_VARIABLE



</td>
<td valign="top">

The predefined session variable cannot be set via the SET command.



</td>
</tr>
<tr>
<td valign="top">

456



</td>
<td valign="top">

ERR\_SQL\_NOT\_ALLOWED\_FOR\_SPECIAL\_ROLE



</td>
<td valign="top">

This action is not allowed for this role.



</td>
</tr>
<tr>
<td valign="top">

457



</td>
<td valign="top">

ERR\_SQL\_DPLC\_CONSTRAINT



</td>
<td valign="top">

Duplicate constraint name.



</td>
</tr>
<tr>
<td valign="top">

458



</td>
<td valign="top">

ERR\_SQL\_UNSUPPORTED\_FUNCTION



</td>
<td valign="top">

Unsupported function included.



</td>
</tr>
<tr>
<td valign="top">

459



</td>
<td valign="top">

ERR\_SQL\_INV\_USABLE\_FUNC



</td>
<td valign="top">

Invalidated function.



</td>
</tr>
<tr>
<td valign="top">

460



</td>
<td valign="top">

ERR\_SQL\_INV\_PRIVILEGE\_FOR\_OBJECT



</td>
<td valign="top">

Invalid privilege for object.



</td>
</tr>
<tr>
<td valign="top">

461



</td>
<td valign="top">

ERR\_SQL\_FK\_NOT\_FOUND



</td>
<td valign="top">

Foreign key constraint violation.



</td>
</tr>
<tr>
<td valign="top">

462



</td>
<td valign="top">

ERR\_SQL\_FK\_ON\_UPDATE\_DELETE\_FAILED



</td>
<td valign="top">

Failed on UPDATE or DELETE by a foreign key constraint violation.



</td>
</tr>
<tr>
<td valign="top">

463



</td>
<td valign="top">

ERR\_SQL\_MAX\_NUM\_TABLE



</td>
<td valign="top">

The number of tables exceeds its maximum.



</td>
</tr>
<tr>
<td valign="top">

464



</td>
<td valign="top">

ERR\_SQL\_MAX\_PARSE\_TREE\_DEPTH



</td>
<td valign="top">

The SQL internal parse tree depth exceeds its maximum.



</td>
</tr>
<tr>
<td valign="top">

465



</td>
<td valign="top">

ERR\_SQL\_INV\_USABLE\_TRIGGER



</td>
<td valign="top">

Cannot execute a trigger that was invalidated by an object change.



</td>
</tr>
<tr>
<td valign="top">

466



</td>
<td valign="top">

ERR\_SQL\_CREDENTIAL\_NOT\_FOUND



</td>
<td valign="top">

No credential found.



</td>
</tr>
<tr>
<td valign="top">

467



</td>
<td valign="top">

ERR\_SQL\_PARAM\_VARIABLE



</td>
<td valign="top">

Cannot use a parameter variable.



</td>
</tr>
<tr>
<td valign="top">

468



</td>
<td valign="top">

ERR\_SQL\_HINT



</td>
<td valign="top">

Hint error.



</td>
</tr>
<tr>
<td valign="top">

469



</td>
<td valign="top">

ERR\_SQL\_INV\_SRC\_DATATYPE



</td>
<td valign="top">

Unsupported data type on the source, consider using a view.



</td>
</tr>
<tr>
<td valign="top">

470



</td>
<td valign="top">

ERR\_SQL\_INV\_DATA\_SOURCE\_CONF



</td>
<td valign="top">

Invalid data source configuration.



</td>
</tr>
<tr>
<td valign="top">

471



</td>
<td valign="top">

ERR\_SQL\_INV\_DATA\_SOURCE



</td>
<td valign="top">

Invalid data source name.



</td>
</tr>
<tr>
<td valign="top">

472



</td>
<td valign="top">

ERR\_SQL\_EXST\_DATA\_SOURCE



</td>
<td valign="top">

Cannot use a duplicate data source name.



</td>
</tr>
<tr>
<td valign="top">

473



</td>
<td valign="top">

ERR\_SQL\_ADAPTER\_CONFIGURATION



</td>
<td valign="top">

Invalid adapter configuration.



</td>
</tr>
<tr>
<td valign="top">

474



</td>
<td valign="top">

ERR\_SQL\_INV\_ADAPTER



</td>
<td valign="top">

Invalid adapter name.



</td>
</tr>
<tr>
<td valign="top">

475



</td>
<td valign="top">

ERR\_SQL\_EXST\_ADAPTER



</td>
<td valign="top">

Cannot use a duplicate adapter name.



</td>
</tr>
<tr>
<td valign="top">

476



</td>
<td valign="top">

ERR\_SQL\_INV\_REMOTE\_OBJECT



</td>
<td valign="top">

Invalid remote object name.



</td>
</tr>
<tr>
<td valign="top">

477



</td>
<td valign="top">

ERR\_SQL\_CREDENTIAL\_EXISTS



</td>
<td valign="top">

The credential already exists.



</td>
</tr>
<tr>
<td valign="top">

478



</td>
<td valign="top">

ERR\_SQL\_UDF\_RUNTIME



</td>
<td valign="top">

User-defined function runtime error.



</td>
</tr>
<tr>
<td valign="top">

479



</td>
<td valign="top">

ERR\_SQL\_INV\_SPATIAL\_ATTRIBUTE



</td>
<td valign="top">

Invalid spatial attribute.



</td>
</tr>
<tr>
<td valign="top">

480



</td>
<td valign="top">

ERR\_SQL\_INV\_SPATIAL\_UNIT



</td>
<td valign="top">

Invalid spatial unit of measure name.



</td>
</tr>
<tr>
<td valign="top">

481



</td>
<td valign="top">

ERR\_SQL\_EXST\_SPATIAL\_UNIT



</td>
<td valign="top">

Cannot use a duplicate spatial unit of measure name.



</td>
</tr>
<tr>
<td valign="top">

482



</td>
<td valign="top">

ERR\_SQL\_INV\_SPATIAL\_REF\_SYS



</td>
<td valign="top">

Invalid spatial reference system name.



</td>
</tr>
<tr>
<td valign="top">

483



</td>
<td valign="top">

ERR\_SQL\_EXST\_SPATIAL\_REF\_SYS



</td>
<td valign="top">

Cannot use a duplicate spatial reference system name.



</td>
</tr>
<tr>
<td valign="top">

484



</td>
<td valign="top">

ERR\_SQL\_SESSION\_GROUP\_COMMAND\_FAILURE



</td>
<td valign="top">

Invalid session group command.



</td>
</tr>
<tr>
<td valign="top">

485



</td>
<td valign="top">

ERR\_SQL\_INV\_STRUCTURED\_PRIVILEGE\_DEFINITION



</td>
<td valign="top">

Invalid definition of structured privilege.



</td>
</tr>
<tr>
<td valign="top">

486



</td>
<td valign="top">

WRN\_SQL\_IMPORT\_PARTIALLY\_FAILED



</td>
<td valign="top">

Some rows have failed to be imported.



</td>
</tr>
<tr>
<td valign="top">

487



</td>
<td valign="top">

ERR\_SQL\_IMPORT\_PARTIALLY\_FAILED



</td>
<td valign="top">

Some of rows have failed to be imported.



</td>
</tr>
<tr>
<td valign="top">

488



</td>
<td valign="top">

ERR\_SQL\_INV\_DATABASE



</td>
<td valign="top">

Invalid database name.



</td>
</tr>
<tr>
<td valign="top">

489



</td>
<td valign="top">

ERR\_SQL\_INV\_EPMMODEL



</td>
<td valign="top">

Invalid EPM Model name.



</td>
</tr>
<tr>
<td valign="top">

490



</td>
<td valign="top">

ERR\_SQL\_EXST\_EPMMODEL



</td>
<td valign="top">

Cannot use a duplicate EPM Model name.



</td>
</tr>
<tr>
<td valign="top">

491



</td>
<td valign="top">

ERR\_SQL\_INV\_EPMMODEL\_DEF



</td>
<td valign="top">

Invalid EPM Model definition.



</td>
</tr>
<tr>
<td valign="top">

492



</td>
<td valign="top">

ERR\_SQL\_INV\_EPMQUERYSOURCE



</td>
<td valign="top">

Invalid EPM Query Source name.



</td>
</tr>
<tr>
<td valign="top">

493



</td>
<td valign="top">

ERR\_SQL\_EXST\_EPMQUERYSOURCE



</td>
<td valign="top">

Cannot use a duplicate EPM Query Source name.



</td>
</tr>
<tr>
<td valign="top">

494



</td>
<td valign="top">

ERR\_SQL\_INV\_EPMQUERYSOURCE\_DEF



</td>
<td valign="top">

Invalid EPM Query Source definition.



</td>
</tr>
<tr>
<td valign="top">

495



</td>
<td valign="top">

ERROR\_SQL\_INVALID\_CONV\_TO\_EXTENDED



</td>
<td valign="top">

The table is already extended with a right delta option.



</td>
</tr>
<tr>
<td valign="top">

496



</td>
<td valign="top">

ERROR\_SQL\_INVALID\_CONV\_FROM\_EXTENDED



</td>
<td valign="top">

The table already specified as non-extended.



</td>
</tr>
<tr>
<td valign="top">

497



</td>
<td valign="top">

ERROR\_EXTENDED\_STORAGE\_NOT\_FOUND



</td>
<td valign="top">

The Extended Storage cannot be found for the table.



</td>
</tr>
<tr>
<td valign="top">

498



</td>
<td valign="top">

ERR\_SQL\_IMPORT\_FAIL\_ON\_MAX\_RECORD\_SIZE\_CHECK



</td>
<td valign="top">

The memory for the record exceeds the limit.



</td>
</tr>
<tr>
<td valign="top">

499



</td>
<td valign="top">

ERR\_SQL\_INV\_C2C



</td>
<td valign="top">

Invalid stacked column search.



</td>
</tr>
<tr>
<td valign="top">

500



</td>
<td valign="top">

ERR\_SQL\_REQUIRE\_PREDICATE



</td>
<td valign="top">

Predicates are required in a WHERE clause.



</td>
</tr>
<tr>
<td valign="top">

501



</td>
<td valign="top">

ERR\_SQL\_SERIES\_INVALID\_SPEC



</td>
<td valign="top">

Invalid series data specification.



</td>
</tr>
<tr>
<td valign="top">

502



</td>
<td valign="top">

ERR\_SQL\_INV\_TASK



</td>
<td valign="top">

Invalid task name.



</td>
</tr>
<tr>
<td valign="top">

503



</td>
<td valign="top">

ERR\_SQL\_EXST\_TASK



</td>
<td valign="top">

Cannot use a duplicate task name.



</td>
</tr>
<tr>
<td valign="top">

504



</td>
<td valign="top">

ERR\_SQL\_INV\_ADAPTER\_LOCATION



</td>
<td valign="top">

Invalid adapter location.



</td>
</tr>
<tr>
<td valign="top">

505



</td>
<td valign="top">

ERR\_SQL\_LAST\_ADAPTER\_LOCATION



</td>
<td valign="top">

Cannot remove the last location of the adapter. Use the DROP ADAPTER statement.



</td>
</tr>
<tr>
<td valign="top">

506



</td>
<td valign="top">

ERR\_SQL\_SYSTEM\_ADAPTER



</td>
<td valign="top">

Invalid CREATE, ALTER, or DROP system adapter.



</td>
</tr>
<tr>
<td valign="top">

507



</td>
<td valign="top">

ERR\_SQL\_INV\_AGENT



</td>
<td valign="top">

Invalid agent name.



</td>
</tr>
<tr>
<td valign="top">

508



</td>
<td valign="top">

ERR\_SQL\_EXST\_AGENT



</td>
<td valign="top">

Cannot use a duplicate agent name.



</td>
</tr>
<tr>
<td valign="top">

509



</td>
<td valign="top">

ERR\_SQL\_INV\_AGENT\_PROPS



</td>
<td valign="top">

Invalid agent properties.



</td>
</tr>
<tr>
<td valign="top">

510



</td>
<td valign="top">

ERR\_SQL\_TEMP\_TABLE\_IN\_USE



</td>
<td valign="top">

Cannot alter a global temporary table in use or a CREATE/ALTER/DROP index on the table.



</td>
</tr>
<tr>
<td valign="top">

512



</td>
<td valign="top">

ERR\_REP



</td>
<td valign="top">

Replication error.



</td>
</tr>
<tr>
<td valign="top">

513



</td>
<td valign="top">

ERR\_SQL\_REP\_ALREADY\_ACTIVE



</td>
<td valign="top">

Cannot execute a DDL statement on a replication table while replicating.



</td>
</tr>
<tr>
<td valign="top">

514



</td>
<td valign="top">

FATAL\_REP\_ANCHOR\_FILE\_FAIL



</td>
<td valign="top">

Failure in accessing the anchor file.



</td>
</tr>
<tr>
<td valign="top">

515



</td>
<td valign="top">

FATAL\_REP\_LOG\_FILE\_FAIL



</td>
<td valign="top">

Failure in accessing the log file.



</td>
</tr>
<tr>
<td valign="top">

516



</td>
<td valign="top">

ERR\_REP\_TABLE\_HAVE\_NOT\_REPORT\_TABLE



</td>
<td valign="top">

The replication table has no conflict report table.



</td>
</tr>
<tr>
<td valign="top">

517



</td>
<td valign="top">

ERR\_REPORT\_TABLE\_ALREADY\_ENABLED



</td>
<td valign="top">

The conflict report table is already enabled.



</td>
</tr>
<tr>
<td valign="top">

518



</td>
<td valign="top">

ERR\_REPORT\_TABLE\_ALREADY\_DISABLED



</td>
<td valign="top">

The conflict report table is already disabled.



</td>
</tr>
<tr>
<td valign="top">

544



</td>
<td valign="top">

ERR\_RS\_PARTITION



</td>
<td valign="top">

Partition error.



</td>
</tr>
<tr>
<td valign="top">

545



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_SPEC



</td>
<td valign="top">

Invalid partition spec.



</td>
</tr>
<tr>
<td valign="top">

546



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_ID



</td>
<td valign="top">

Invalid partition id.



</td>
</tr>
<tr>
<td valign="top">

547



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_PROPERTY



</td>
<td valign="top">

Invalid use of partition property.



</td>
</tr>
<tr>
<td valign="top">

548



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_RANGE



</td>
<td valign="top">

Invalid partition range.



</td>
</tr>
<tr>
<td valign="top">

549



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_TYPE



</td>
<td valign="top">

Invalid partition type.



</td>
</tr>
<tr>
<td valign="top">

550



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_COLUMN



</td>
<td valign="top">

Invalid partition column.



</td>
</tr>
<tr>
<td valign="top">

551



</td>
<td valign="top">

ERR\_RS\_PARTITION\_INVALID\_LEVEL



</td>
<td valign="top">

Invalid partition level.



</td>
</tr>
<tr>
<td valign="top">

576



</td>
<td valign="top">

ERR\_API



</td>
<td valign="top">

API error.



</td>
</tr>
<tr>
<td valign="top">

577



</td>
<td valign="top">

ERR\_API\_NO\_CURSOR\_FWD



</td>
<td valign="top">

The cursor type of forward is not allowed.



</td>
</tr>
<tr>
<td valign="top">

578



</td>
<td valign="top">

ERR\_API\_INV\_STATEMENT



</td>
<td valign="top">

Invalid statement.



</td>
</tr>
<tr>
<td valign="top">

579



</td>
<td valign="top">

ERR\_API\_EXCEED\_MAX\_GROUP\_SIZE



</td>
<td valign="top">

You have exceeded the maximum batch size.



</td>
</tr>
<tr>
<td valign="top">

580



</td>
<td valign="top">

ERR\_API\_VERSION\_INCOMPATIBLE



</td>
<td valign="top">

The server rejected the connection \(there was a protocol version mismatch\).



</td>
</tr>
<tr>
<td valign="top">

581



</td>
<td valign="top">

ERR\_API\_ONLY\_SINGLE\_STATEMENT



</td>
<td valign="top">

This function can only be called in the case of single statement.



</td>
</tr>
<tr>
<td valign="top">

582



</td>
<td valign="top">

ERR\_API\_INV\_RETURN\_OBJECT



</td>
<td valign="top">

This query does not have a result set.



</td>
</tr>
<tr>
<td valign="top">

583



</td>
<td valign="top">

ERR\_API\_CONNECTION\_DOES\_NOT\_EXIST



</td>
<td valign="top">

The connection does not exist.



</td>
</tr>
<tr>
<td valign="top">

584



</td>
<td valign="top">

ERR\_API\_NO\_MORE\_LOB\_DATA



</td>
<td valign="top">

There is no more LOB data.



</td>
</tr>
<tr>
<td valign="top">

585



</td>
<td valign="top">

ERR\_API\_OPERATION\_NOT\_PERMITTED



</td>
<td valign="top">

This operation is not permitted.



</td>
</tr>
<tr>
<td valign="top">

586



</td>
<td valign="top">

ERR\_API\_INV\_PARAMETER\_FROM\_SERVER



</td>
<td valign="top">

There was an invalid parameter received from the server.



</td>
</tr>
<tr>
<td valign="top">

587



</td>
<td valign="top">

ERR\_API\_INV\_RESULTSET



</td>
<td valign="top">

The result set is currently invalid.



</td>
</tr>
<tr>
<td valign="top">

588



</td>
<td valign="top">

ERR\_API\_RESULTSET\_NEXT\_NOT\_CALLED



</td>
<td valign="top">

Next\(\) is not called for this result set.



</td>
</tr>
<tr>
<td valign="top">

589



</td>
<td valign="top">

ERR\_API\_TOO\_MANY\_PARAMETERS



</td>
<td valign="top">

Too many parameters are set.



</td>
</tr>
<tr>
<td valign="top">

590



</td>
<td valign="top">

ERR\_API\_MISSING\_PARAMETER



</td>
<td valign="top">

Some parameters are missing.



</td>
</tr>
<tr>
<td valign="top">

591



</td>
<td valign="top">

ERR\_API\_INTERNAL\_ERROR



</td>
<td valign="top">

Internal API error.



</td>
</tr>
<tr>
<td valign="top">

592



</td>
<td valign="top">

ERR\_API\_NOT\_SUPPORTED\_TYPECONV



</td>
<td valign="top">

This is not a supported type conversion.



</td>
</tr>
<tr>
<td valign="top">

593



</td>
<td valign="top">

ERR\_API\_REMOTE\_ONLY



</td>
<td valign="top">

This is a remote-only function.



</td>
</tr>
<tr>
<td valign="top">

594



</td>
<td valign="top">

ERR\_API\_NO\_MORE\_RESULT\_ROW



</td>
<td valign="top">

There are no more result rows in the result set.



</td>
</tr>
<tr>
<td valign="top">

595



</td>
<td valign="top">

ERR\_API\_NOT\_OUT\_PARAM



</td>
<td valign="top">

The specified parameter is not an output parameter.



</td>
</tr>
<tr>
<td valign="top">

596



</td>
<td valign="top">

ERR\_API\_LOB\_STREAM\_NOT\_PERMITTED



</td>
<td valign="top">

LOB streaming is not permitted in auto-commit mode.



</td>
</tr>
<tr>
<td valign="top">

597



</td>
<td valign="top">

ERR\_API\_SESSION\_CONTEXT\_ERROR



</td>
<td valign="top">

There is a session context error.



</td>
</tr>
<tr>
<td valign="top">

598



</td>
<td valign="top">

ERR\_API\_EXTERNAL\_EXECUTION\_FAILURE



</td>
<td valign="top">

Failed to execute the external statement.



</td>
</tr>
<tr>
<td valign="top">

599



</td>
<td valign="top">

ERR\_API\_NOT\_INITIALIZED



</td>
<td valign="top">

The session layer is not initialized yet.



</td>
</tr>
<tr>
<td valign="top">

600



</td>
<td valign="top">

ERR\_API\_CALL\_ROUTING\_FAILURE



</td>
<td valign="top">

Failed routed execution.



</td>
</tr>
<tr>
<td valign="top">

601



</td>
<td valign="top">

ERR\_API\_TOO\_MANY\_SESSION\_VARIABLES



</td>
<td valign="top">

Too many session variables are set.



</td>
</tr>
<tr>
<td valign="top">

602



</td>
<td valign="top">

ERR\_API\_READONLY\_SESSION\_VARIABLE



</td>
<td valign="top">

Cannot set read-only session variables.



</td>
</tr>
<tr>
<td valign="top">

603



</td>
<td valign="top">

ERR\_API\_INV\_LOB



</td>
<td valign="top">

Invalid LOB.



</td>
</tr>
<tr>
<td valign="top">

604



</td>
<td valign="top">

ERR\_API\_REMOTE\_TEMP\_TABLE



</td>
<td valign="top">

There is a remote temporary table access failure.



</td>
</tr>
<tr>
<td valign="top">

605



</td>
<td valign="top">

ERR\_API\_INV\_XA\_JOIN



</td>
<td valign="top">

Invalid XA join request.



</td>
</tr>
<tr>
<td valign="top">

606



</td>
<td valign="top">

ERR\_API\_EXCEED\_MAX\_LOB\_SIZE



</td>
<td valign="top">

You have exceeded the maximum LOB size.



</td>
</tr>
<tr>
<td valign="top">

607



</td>
<td valign="top">

ERR\_API\_CLEANUP\_RESOURCE



</td>
<td valign="top">

Failed to cleanup resources.



</td>
</tr>
<tr>
<td valign="top">

608



</td>
<td valign="top">

ERR\_API\_EXCEED\_MAX\_PREPARED\_STATEMENT



</td>
<td valign="top">

You have exceeded the maximum number of prepared statements.



</td>
</tr>
<tr>
<td valign="top">

609



</td>
<td valign="top">

ERR\_API\_INVALID\_CESU8\_STRING



</td>
<td valign="top">

Invalid CESU-8 string.



</td>
</tr>
<tr>
<td valign="top">

610



</td>
<td valign="top">

ERR\_API\_ROLLBACK\_FAILURE



</td>
<td valign="top">

There is a transaction rollback failure.



</td>
</tr>
<tr>
<td valign="top">

611



</td>
<td valign="top">

ERR\_API\_SESSION\_VARIABLE\_VALUE\_LENGTH\_EXCEEDED



</td>
<td valign="top">

You have exceeded the maximum value length for the session variable.



</td>
</tr>
<tr>
<td valign="top">

612



</td>
<td valign="top">

ERR\_API\_SESSION\_VARIABLE\_KEY\_LENGTH\_EXCEEDED



</td>
<td valign="top">

You have exceeded the maximum key length for the session variable.



</td>
</tr>
<tr>
<td valign="top">

613



</td>
<td valign="top">

ERR\_API\_TIMEOUT



</td>
<td valign="top">

The execution was aborted by a timeout.



</td>
</tr>
<tr>
<td valign="top">

614



</td>
<td valign="top">

ERR\_API\_ACCESS\_ENCRYPTED\_DATA



</td>
<td valign="top">

Encrypted data access is not permitted.



</td>
</tr>
<tr>
<td valign="top">

615



</td>
<td valign="top">

ERR\_API\_REMOTE\_CONNECTION\_DOES\_NOT\_EXIST



</td>
<td valign="top">

The remote connection does not exist.



</td>
</tr>
<tr>
<td valign="top">

640



</td>
<td valign="top">

ERR\_SQL\_2



</td>
<td valign="top">

SQL processing error.



</td>
</tr>
<tr>
<td valign="top">

641



</td>
<td valign="top">

ERR\_SQL\_INV\_REMOTE\_SUBSCRIPTION



</td>
<td valign="top">

Invalid remote subscription name.



</td>
</tr>
<tr>
<td valign="top">

642



</td>
<td valign="top">

ERR\_SQL\_EXST\_REMOTE\_SUBSCRIPTION



</td>
<td valign="top">

Cannot use duplicate remote subscription names.



</td>
</tr>
<tr>
<td valign="top">

643



</td>
<td valign="top">

ERR\_SQL\_INV\_REMOTE\_SUBSCRIPTION\_DEF



</td>
<td valign="top">

Invalid remote subscription definition.



</td>
</tr>
<tr>
<td valign="top">

644



</td>
<td valign="top">

ERR\_SQL\_EXST\_REMOTE\_SOURCE\_ADAPTER\_LOCATION



</td>
<td valign="top">

The remote source refers to the adapter location.



</td>
</tr>
<tr>
<td valign="top">

645



</td>
<td valign="top">

ERR\_SQL\_EXST\_REMOTE\_SOURCE\_ACTIVE\_SUBSCRIPTIONS



</td>
<td valign="top">

The remote source has active remote subscriptions.



</td>
</tr>
<tr>
<td valign="top">

646



</td>
<td valign="top">

ERR\_SQL\_INV\_USABLE\_TASK



</td>
<td valign="top">

Invalidated task.



</td>
</tr>
<tr>
<td valign="top">

647



</td>
<td valign="top">

ERR\_SQL\_NOT\_ALLOWED\_SYNTAX\_FOR\_TRIGGER



</td>
<td valign="top">

The syntax is not supported in the trigger.



</td>
</tr>
<tr>
<td valign="top">

648



</td>
<td valign="top">

ERR\_SQL\_TRIGGER\_AND\_PROC\_NESTING\_DEPTH\_EXCEEDED



</td>
<td valign="top">

You have exceeded the nesting depth of the trigger and the procedure.



</td>
</tr>
<tr>
<td valign="top">

649



</td>
<td valign="top">

ERR\_SQL\_QUERY\_PINNED\_PLAN



</td>
<td valign="top">

Pinned plan error.



</td>
</tr>
<tr>
<td valign="top">

650



</td>
<td valign="top">

ERR\_SQL\_QUERY\_REMOVE\_PINNED\_PLAN



</td>
<td valign="top">

Remove pinned plan error.



</td>
</tr>
<tr>
<td valign="top">

651



</td>
<td valign="top">

ERR\_SQL\_EXST\_OBJECT



</td>
<td valign="top">

Cannot use duplicate object name.



</td>
</tr>
<tr>
<td valign="top">

652



</td>
<td valign="top">

ERR\_SQL\_AMBG\_SCHEMA



</td>
<td valign="top">

The schema is ambiguously defined.



</td>
</tr>
<tr>
<td valign="top">

653



</td>
<td valign="top">

ERR\_SQL\_SET\_ROW\_ORDER



</td>
<td valign="top">

The row order is already set on the table.



</td>
</tr>
<tr>
<td valign="top">

654



</td>
<td valign="top">

ERR\_SQL\_NO\_ROW\_ORDER



</td>
<td valign="top">

There is no row order set on the table.



</td>
</tr>
<tr>
<td valign="top">

655



</td>
<td valign="top">

ERR\_SQL\_LICENSING\_RUNTIME



</td>
<td valign="top">

Licensing error.



</td>
</tr>
<tr>
<td valign="top">

656



</td>
<td valign="top">

ERR\_SQL\_LONG\_PROPERTY



</td>
<td valign="top">

The property value is too long.



</td>
</tr>
<tr>
<td valign="top">

657



</td>
<td valign="top">

ERR\_SQL\_CANCEL\_TASK\_TIMEOUT\_REACHED



</td>
<td valign="top">

The request to cancel the task was sent but the task did not cancel before the timeout was reached.



</td>
</tr>
<tr>
<td valign="top">

658



</td>
<td valign="top">

ERR\_SQL\_CANNOT\_MUTATE\_TABLE\_DURING\_FK\_EXECUTION



</td>
<td valign="top">

Cannot mutate the table during trigger or foreign key execution.



</td>
</tr>
<tr>
<td valign="top">

659



</td>
<td valign="top">

ERR\_SQL\_EXST\_WORKLOAD\_CLASS



</td>
<td valign="top">

Cannot use duplicate workload class name.



</td>
</tr>
<tr>
<td valign="top">

660



</td>
<td valign="top">

ERR\_SQL\_INV\_WORKLOAD\_CLASS



</td>
<td valign="top">

Invalid workload class name.



</td>
</tr>
<tr>
<td valign="top">

661



</td>
<td valign="top">

ERR\_SQL\_EXST\_WORKLOAD\_MAPPING



</td>
<td valign="top">

Cannot use duplicate workload mapping names.



</td>
</tr>
<tr>
<td valign="top">

662



</td>
<td valign="top">

ERR\_SQL\_INV\_WORKLOAD\_MAPPING



</td>
<td valign="top">

Invalid workload mapping name.



</td>
</tr>
<tr>
<td valign="top">

663



</td>
<td valign="top">

ERR\_SQL\_CONNECT\_NOT\_ALLOWED



</td>
<td valign="top">

The user is not allowed to connect from the client.



</td>
</tr>
<tr>
<td valign="top">

664



</td>
<td valign="top">

ERR\_SQL\_INV\_AGENT\_GROUP



</td>
<td valign="top">

Invalid agent group name.



</td>
</tr>
<tr>
<td valign="top">

665



</td>
<td valign="top">

ERR\_SQL\_EXST\_AGENT\_GROUP



</td>
<td valign="top">

Cannot use duplicate agent group names.



</td>
</tr>
<tr>
<td valign="top">

666



</td>
<td valign="top">

ERR\_SQL\_AGENT\_GROUP\_NOT\_EMPTY



</td>
<td valign="top">

The agents are still set to this agent group.



</td>
</tr>
<tr>
<td valign="top">

668



</td>
<td valign="top">

ERR\_SQL\_2D\_POINTS\_SUPPORTED\_ONLY



</td>
<td valign="top">

ST\_Point columns only support 2-dimensional points.



</td>
</tr>
<tr>
<td valign="top">

669



</td>
<td valign="top">

ERR\_SQL\_SPATIAL\_ERROR



</td>
<td valign="top">

Spatial error.



</td>
</tr>
<tr>
<td valign="top">

670



</td>
<td valign="top">

ERR\_SQL\_PART\_NOT\_EXIST



</td>
<td valign="top">

The part does not exist.



</td>
</tr>
<tr>
<td valign="top">

671



</td>
<td valign="top">

ERR\_SQL\_EXST\_LIBRARY



</td>
<td valign="top">

Cannot use duplicate library names.



</td>
</tr>
<tr>
<td valign="top">

672



</td>
<td valign="top">

ERR\_SQL\_DPLC\_ASSOCIATION



</td>
<td valign="top">

Duplicate association names.



</td>
</tr>
<tr>
<td valign="top">

673



</td>
<td valign="top">

ERR\_SQL\_INV\_GRAPH\_WORKSPACE



</td>
<td valign="top">

Invalid graph workspace name.



</td>
</tr>
<tr>
<td valign="top">

674



</td>
<td valign="top">

WRN\_SQL\_EXPORT\_SKIP\_CROSSDB\_OBJECT



</td>
<td valign="top">

The cross database object found and skipped in exporting might cause IMPORT to fail.



</td>
</tr>
<tr>
<td valign="top">

675



</td>
<td valign="top">

ERR\_SQL\_EXST\_GRAPH\_WORKSPACE



</td>
<td valign="top">

Cannot use duplicate graph workspace names.



</td>
</tr>
<tr>
<td valign="top">

676



</td>
<td valign="top">

ERR\_SQL\_DUP\_WORKLOAD\_MAPPING



</td>
<td valign="top">

Cannot use duplicate workload mappings to the same combination of: user name, application user name, application name, client application, component name, or application component type.



</td>
</tr>
<tr>
<td valign="top">

677



</td>
<td valign="top">

ERR\_SQL\_CHECK\_CONSTRAINT\_VIOLATION



</td>
<td valign="top">

Check the constraint violation.



</td>
</tr>
<tr>
<td valign="top">

678



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stabilizer error.



</td>
</tr>
<tr>
<td valign="top">

679



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_NO\_MANAGER\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stabilizer error - manager not found. Check if the Plan Stabilizer is enabled.



</td>
</tr>
<tr>
<td valign="top">

680



</td>
<td valign="top">

ERR\_SQL\_STATEMENT\_HINT



</td>
<td valign="top">

Statement hint error.



</td>
</tr>
<tr>
<td valign="top">

681



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_HINT\_COMMAND



</td>
<td valign="top">

Plan stabilizer stored hint error - error while processing the statement hint command.



</td>
</tr>
<tr>
<td valign="top">

682



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_HINT\_TABLE\_EMPTY



</td>
<td valign="top">

Plan stabilizer stored hint error - the statement hint table is empty.



</td>
</tr>
<tr>
<td valign="top">

683



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_HINT\_MAP\_LOAD\_ERROR



</td>
<td valign="top">

Plan stabilizer stored hint error - the statement hint table is corrupt.



</td>
</tr>
<tr>
<td valign="top">

684



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_HINT\_RECORD\_ALREADY\_EXISTS



</td>
<td valign="top">

Plan stabilizer stored hint error - the statement hint record already exists.



</td>
</tr>
<tr>
<td valign="top">

685



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_HINT\_RECORD\_DOES\_NOT\_EXIST



</td>
<td valign="top">

Plan stabilizer stored hint error - the statement hint record does not exist.



</td>
</tr>
<tr>
<td valign="top">

686



</td>
<td valign="top">

ERR\_SQL\_START\_TASK\_ERROR



</td>
<td valign="top">

Start task error.



</td>
</tr>
<tr>
<td valign="top">

687



</td>
<td valign="top">

ERR\_SQL\_EXCEED\_LAG\_TIME



</td>
<td valign="top">

You have exceeded the lag time of RESULT\_LAG.



</td>
</tr>
<tr>
<td valign="top">

688



</td>
<td valign="top">

ERR\_IO\_FAILURE\_ON\_FILE\_WRITE



</td>
<td valign="top">

I/O error occurred on the file write.



</td>
</tr>
<tr>
<td valign="top">

689



</td>
<td valign="top">

ERR\_SQL\_DUPLICATE\_ROWID\_MATCHED



</td>
<td valign="top">

Duplicate ROWID matched during the merge.



</td>
</tr>
<tr>
<td valign="top">

690



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_PLAN\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stabilizer stored plan error.



</td>
</tr>
<tr>
<td valign="top">

691



</td>
<td valign="top">

ERR\_SQL\_PLANSTABILIZER\_STORED\_PLAN\_COMMAND\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stabilizer stored plan error - error while processing command.



</td>
</tr>
<tr>
<td valign="top">

692



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_TABLE\_EMPTY\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stabilizer stored plan error - stored plan table is empty.



</td>
</tr>
<tr>
<td valign="top">

693



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_MAP\_LOAD\_ERROR\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stability error - stored plan table is corrupt.



</td>
</tr>
<tr>
<td valign="top">

694



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_RECORD\_ALREADY\_EXISTS\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stability error - stored plan record already exists.



</td>
</tr>
<tr>
<td valign="top">

695



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_RECORD\_DOES\_NOT\_EXIST\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stability error - stored plan record does not exist.



</td>
</tr>
<tr>
<td valign="top">

696



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_CANNOT\_CONVERT\_ABSTRACT\_PLAN\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stability error - cannot convert to abstract plan.



</td>
</tr>
<tr>
<td valign="top">

697



</td>
<td valign="top">

ERR\_SQL\_PREACTIVE\_KEY\_EXISTS



</td>
<td valign="top">

Preactive key already exists.



</td>
</tr>
<tr>
<td valign="top">

698



</td>
<td valign="top">

ERR\_SQL\_NO\_PREACTIVE\_KEY



</td>
<td valign="top">

No preactive key exists.



</td>
</tr>
<tr>
<td valign="top">

699



</td>
<td valign="top">

ERR\_SQL\_EXST\_DEPENDENCY\_RULE



</td>
<td valign="top">

Cannot use a duplicate dependency rule name.



</td>
</tr>
<tr>
<td valign="top">

700



</td>
<td valign="top">

ERR\_SQL\_SINGLE\_COLUMN\_SEARCH\_THROW\_ERROR



</td>
<td valign="top">

There is no stacked column search \(throw\_error\) error.



</td>
</tr>
<tr>
<td valign="top">

701



</td>
<td valign="top">

ERR\_SQL\_EXST\_USERGROUP



</td>
<td valign="top">

The usergroup name already exists.



</td>
</tr>
<tr>
<td valign="top">

702



</td>
<td valign="top">

ERR\_SQL\_INV\_USERGROUP



</td>
<td valign="top">

Invalid usergroup name.



</td>
</tr>
<tr>
<td valign="top">

703



</td>
<td valign="top">

ERR\_INCORRECT\_ROOT\_KEYS\_BACKUP\_PASSWORD



</td>
<td valign="top">

Incorrect root keys backup password.



</td>
</tr>
<tr>
<td valign="top">

704



</td>
<td valign="top">

ERR\_SQL\_USERGROUP\_DELETION\_FAILED



</td>
<td valign="top">

The usergroup cannot be dropped.



</td>
</tr>
<tr>
<td valign="top">

705



</td>
<td valign="top">

ERR\_SQL\_CONCURRENT\_GRANT



</td>
<td valign="top">

Two concurrent statements performed the same GRANT operation.



</td>
</tr>
<tr>
<td valign="top">

706



</td>
<td valign="top">

ERR\_SQL\_INV\_SYMMETRIC\_CIPHER



</td>
<td valign="top">

Only AES-256-CBC is supported: invalid cipher.



</td>
</tr>
<tr>
<td valign="top">

707



</td>
<td valign="top">

ERR\_SQL\_EXST\_COLUMN\_KEY



</td>
<td valign="top">

Cannot use duplicate column key names.



</td>
</tr>
<tr>
<td valign="top">

708



</td>
<td valign="top">

ERR\_SQL\_EXST\_COLUMN\_KEYCOPY



</td>
<td valign="top">

The `keycopy` column already exists.



</td>
</tr>
<tr>
<td valign="top">

709



</td>
<td valign="top">

ERR\_SQL\_EXST\_KEYPAIR



</td>
<td valign="top">

The `keypair` column already exists.



</td>
</tr>
<tr>
<td valign="top">

710



</td>
<td valign="top">

ERR\_SQL\_INV\_ASYMMETRIC\_CIPHER



</td>
<td valign="top">

Only RSA-OAEP-2048 is supported: invalid cipher.



</td>
</tr>
<tr>
<td valign="top">

711



</td>
<td valign="top">

ERR\_SQL\_EXST\_COLUMN\_KEY\_ID



</td>
<td valign="top">

Cannot use duplicate column key IDs.



</td>
</tr>
<tr>
<td valign="top">

712



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_MIGRATION\_DEPRECATED



</td>
<td valign="top">

Deprecated plan stabilizer stored plan error - migration error.



</td>
</tr>
<tr>
<td valign="top">

713



</td>
<td valign="top">

ERR\_SQL\_NOT\_OWN\_KEYPAIR



</td>
<td valign="top">

The `keypair` column is not owned by the creator of the column key.



</td>
</tr>
<tr>
<td valign="top">

714



</td>
<td valign="top">

ERR\_SQL\_DROP\_COLUMN\_KEYCOPY



</td>
<td valign="top">

Cannot drop the last key admin `keycopy`.



</td>
</tr>
<tr>
<td valign="top">

715



</td>
<td valign="top">

ERR\_SQL\_EMPTY\_WORKLOAD\_MAPPING



</td>
<td valign="top">

Cannot use a workload mapping with no properties.



</td>
</tr>
<tr>
<td valign="top">

716



</td>
<td valign="top">

ERR\_SQL\_STALE\_STATEMENT



</td>
<td valign="top">

The statement has stale metadata or the column encryption key of some columns have changed.



</td>
</tr>
<tr>
<td valign="top">

717



</td>
<td valign="top">

ERR\_SQL\_INV\_KEY\_ID



</td>
<td valign="top">

Invalid key ID.



</td>
</tr>
<tr>
<td valign="top">

718



</td>
<td valign="top">

ERR\_SQL\_CANNOT\_UPDATE\_NOT\_EXISTING\_ROW



</td>
<td valign="top">

Cannot update a non-existent row.



</td>
</tr>
<tr>
<td valign="top">

719



</td>
<td valign="top">

ERR\_SQL\_CURRENCY\_UNIT\_CONVERSION



</td>
<td valign="top">

Currency/unit conversion error.



</td>
</tr>
<tr>
<td valign="top">

720



</td>
<td valign="top">

ERR\_SQL\_DDL\_DISABLED



</td>
<td valign="top">

DDL is currently disabled in this session.



</td>
</tr>
<tr>
<td valign="top">

721



</td>
<td valign="top">

ERR\_SQL\_MISSING\_ROWID



</td>
<td valign="top">

The row ID column is not found.



</td>
</tr>
<tr>
<td valign="top">

722



</td>
<td valign="top">

ERR\_SQL\_DROP\_LAST\_COLUMN\_KEYCOPY



</td>
<td valign="top">

Cannot drop the last keycopy.



</td>
</tr>
<tr>
<td valign="top">

723



</td>
<td valign="top">

ERR\_SQL\_NOT\_KEY\_ADMIN\_KEYPAIR



</td>
<td valign="top">

The keypair is not owned by the key admin.



</td>
</tr>
<tr>
<td valign="top">

724



</td>
<td valign="top">

ERR\_SQL\_INV\_LIBRARY



</td>
<td valign="top">

Invalid library name.



</td>
</tr>
<tr>
<td valign="top">

725



</td>
<td valign="top">

ERR\_SQL\_INV\_USABLE\_LIBRARY



</td>
<td valign="top">

Invalidated library.



</td>
</tr>
<tr>
<td valign="top">

1024



</td>
<td valign="top">

ERR\_SES



</td>
<td valign="top">

Session error.



</td>
</tr>
<tr>
<td valign="top">

1025



</td>
<td valign="top">

ERR\_COM



</td>
<td valign="top">

Communication error.



</td>
</tr>
<tr>
<td valign="top">

1026



</td>
<td valign="top">

ERR\_COM\_LISTEN



</td>
<td valign="top">

Cannot bind a communication port.



</td>
</tr>
<tr>
<td valign="top">

1027



</td>
<td valign="top">

ERR\_COM\_INIT



</td>
<td valign="top">

Communication initialization error.



</td>
</tr>
<tr>
<td valign="top">

1028



</td>
<td valign="top">

ERR\_COM\_IOCTL



</td>
<td valign="top">

I/O control error.



</td>
</tr>
<tr>
<td valign="top">

1029



</td>
<td valign="top">

ERR\_COM\_CONNECT



</td>
<td valign="top">

Connection failure.



</td>
</tr>
<tr>
<td valign="top">

1030



</td>
<td valign="top">

ERR\_COM\_SEND



</td>
<td valign="top">

Send error.



</td>
</tr>
<tr>
<td valign="top">

1031



</td>
<td valign="top">

ERR\_COM\_RECEIVE



</td>
<td valign="top">

Receive error.



</td>
</tr>
<tr>
<td valign="top">

1032



</td>
<td valign="top">

ERR\_SES\_THREAD\_CREATE



</td>
<td valign="top">

Cannot create a thread.



</td>
</tr>
<tr>
<td valign="top">

1033



</td>
<td valign="top">

ERR\_SES\_INV\_PROTOCOL



</td>
<td valign="top">

Error while parsing the protocol.



</td>
</tr>
<tr>
<td valign="top">

1034



</td>
<td valign="top">

ERR\_SES\_EXCEED\_MAX\_SESSION



</td>
<td valign="top">

You have exceeded the maximum number of sessions.



</td>
</tr>
<tr>
<td valign="top">

1035



</td>
<td valign="top">

ERR\_SES\_INV\_VERSION



</td>
<td valign="top">

The version is not supported.



</td>
</tr>
<tr>
<td valign="top">

1036



</td>
<td valign="top">

ERR\_SES\_INV\_SESSION



</td>
<td valign="top">

Invalid session ID.



</td>
</tr>
<tr>
<td valign="top">

1037



</td>
<td valign="top">

ERR\_COM\_UNKNOWN\_HOST



</td>
<td valign="top">

Unknown hostname.



</td>
</tr>
<tr>
<td valign="top">

1038



</td>
<td valign="top">

ERR\_SES\_SERVER\_BUSY



</td>
<td valign="top">

The server is temporarily overloaded.



</td>
</tr>
<tr>
<td valign="top">

1088



</td>
<td valign="top">

ERR\_DATA\_STAT



</td>
<td valign="top">

Data statistics error.



</td>
</tr>
<tr>
<td valign="top">

1089



</td>
<td valign="top">

ERR\_DATA\_STAT\_NOT\_FOUND



</td>
<td valign="top">

No matching data statistics objects found.



</td>
</tr>
<tr>
<td valign="top">

1090



</td>
<td valign="top">

ERR\_DATA\_STAT\_REMOTE\_QUERY\_ERR



</td>
<td valign="top">

Invalid results from the query to the remote source.



</td>
</tr>
<tr>
<td valign="top">

1091



</td>
<td valign="top">

ERR\_DATA\_STAT\_TABLE\_NOT\_FOUND



</td>
<td valign="top">

The specified table is not found or not supported.



</td>
</tr>
<tr>
<td valign="top">

1092



</td>
<td valign="top">

ERR\_DATA\_STAT\_BUILD\_ERROR



</td>
<td valign="top">

Error building data statistics object.



</td>
</tr>
<tr>
<td valign="top">

1093



</td>
<td valign="top">

ERR\_DATA\_STAT\_EXISTS



</td>
<td valign="top">

The data statistics object already exists.



</td>
</tr>
<tr>
<td valign="top">

1094



</td>
<td valign="top">

ERR\_DATA\_STAT\_INVALID\_SETTING



</td>
<td valign="top">

There is an invalid combination of settings specified.



</td>
</tr>
<tr>
<td valign="top">

1120



</td>
<td valign="top">

ERR\_USERGROUP\_GENERAL



</td>
<td valign="top">

Usergroup error.



</td>
</tr>
<tr>
<td valign="top">

1121



</td>
<td valign="top">

ERR\_USERGROUP\_USER\_NOT\_MEMBER\_OF\_ANY



</td>
<td valign="top">

The user is not a member of any usergroup.



</td>
</tr>
<tr>
<td valign="top">

1122



</td>
<td valign="top">

ERR\_USERGROUP\_EQUAL\_CURRENT\_AND\_NEW\_USERGROUP



</td>
<td valign="top">

The current and new usergroup are the same.



</td>
</tr>
<tr>
<td valign="top">

1123



</td>
<td valign="top">

ERR\_USERGROUP\_UNKNOWN\_PARAMETER\_NAME



</td>
<td valign="top">

There is an unknown parameter for the usergroup.



</td>
</tr>
<tr>
<td valign="top">

1124



</td>
<td valign="top">

ERR\_USERGROUP\_UNKNOWN\_PARAMETER\_SET\_NAME



</td>
<td valign="top">

An unknown parameter is set for the usergroup.



</td>
</tr>
<tr>
<td valign="top">

1125



</td>
<td valign="top">

ERR\_USERGROUP\_DUPLICATE\_PARAMETER\_NAME



</td>
<td valign="top">

The same parameter name is specified more than once.



</td>
</tr>
<tr>
<td valign="top">

1126



</td>
<td valign="top">

ERR\_USERGROUP\_INVALID\_PARAMETER\_VALUE



</td>
<td valign="top">

Invalid value for the usergroup parameter.



</td>
</tr>
<tr>
<td valign="top">

1152



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY



</td>
<td valign="top">

Plan stability error.



</td>
</tr>
<tr>
<td valign="top">

1153



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_COMMAND



</td>
<td valign="top">

Plan stability error - cannot execute the command.



</td>
</tr>
<tr>
<td valign="top">

1154



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_TABLE\_EMPTY



</td>
<td valign="top">

Plan stability error - the abstract SQL plan table is empty.



</td>
</tr>
<tr>
<td valign="top">

1155



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_MAP\_LOAD\_ERROR



</td>
<td valign="top">

Plan stability error - cannot load the abstract SQL plan.



</td>
</tr>
<tr>
<td valign="top">

1156



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_RECORD\_ALREADY\_EXISTS



</td>
<td valign="top">

Plan stability error - the abstract SQL plan record already exists.



</td>
</tr>
<tr>
<td valign="top">

1157



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_RECORD\_DOES\_NOT\_EXIST



</td>
<td valign="top">

Plan stability error - the abstract SQL plan record does not exist.



</td>
</tr>
<tr>
<td valign="top">

1158



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_CANNOT\_CAPTURE



</td>
<td valign="top">

Plan stability error - cannot capture the plan.



</td>
</tr>
<tr>
<td valign="top">

1159



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_MIGRATION



</td>
<td valign="top">

Plan stability error - migration.



</td>
</tr>
<tr>
<td valign="top">

1160



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_CANNOT\_APPLY



</td>
<td valign="top">

Plan stability error - cannot apply using abstract SQL plan.



</td>
</tr>
<tr>
<td valign="top">

1161



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_JSON\_ERROR



</td>
<td valign="top">

Plan stability error - cannot deserialize the captured JSON.



</td>
</tr>
<tr>
<td valign="top">

1162



</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_UPDATE\_LOCATION



</td>
<td valign="top">

Plan stability error - update location first.



</td>
</tr>
<tr>
<td valign="top">

1280



</td>
<td valign="top">

ERR\_SQLSCRIPT\_2



</td>
<td valign="top">

SQLscript error.



</td>
</tr>
<tr>
<td valign="top">

1281



</td>
<td valign="top">

ERR\_SQLSCRIPT\_WRONG\_PARAMS



</td>
<td valign="top">

There is an incorrect number or types of parameters in call.



</td>
</tr>
<tr>
<td valign="top">

1282



</td>
<td valign="top">

ERR\_SQLSCRIPT\_OUT\_PARAM\_VAR



</td>
<td valign="top">

The output parameter is not a variable.



</td>
</tr>
<tr>
<td valign="top">

1283



</td>
<td valign="top">

ERR\_SQLSCRIPT\_OUT\_PARAM\_DEFAULT



</td>
<td valign="top">

The OUT and IN OUT parameters may not have default expressions.



</td>
</tr>
<tr>
<td valign="top">

1284



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DUP\_PARAMETERS



</td>
<td valign="top">

Duplicate parameters are not permitted.



</td>
</tr>
<tr>
<td valign="top">

1285



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DUP\_DECL



</td>
<td valign="top">

At most one declaration is permitted in the declaration section.



</td>
</tr>
<tr>
<td valign="top">

1286



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CURSOR\_SELECT\_STMT



</td>
<td valign="top">

The cursor must be declared by a SELECT statement.



</td>
</tr>
<tr>
<td valign="top">

1287



</td>
<td valign="top">

ERR\_SQLSCRIPT\_ID\_NOT\_DECLARED



</td>
<td valign="top">

An identifier must be declared.



</td>
</tr>
<tr>
<td valign="top">

1288



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ASSIGN\_TARGET



</td>
<td valign="top">

The expression cannot be used as an assignment target.



</td>
</tr>
<tr>
<td valign="top">

1289



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_INTO\_TARGET



</td>
<td valign="top">

The expression cannot be used as an INTO-target of the SELECT/FETCH statement.



</td>
</tr>
<tr>
<td valign="top">

1290



</td>
<td valign="top">

ERR\_SQLSCRIPT\_LHS\_CANNOT\_ASSIGNED



</td>
<td valign="top">

The expression is inappropriate as the left-hand side of an assignment statement.



</td>
</tr>
<tr>
<td valign="top">

1291



</td>
<td valign="top">

ERR\_SQLSCRIPT\_EXPR\_WRONG\_TYPE



</td>
<td valign="top">

Incorrect expression type.



</td>
</tr>
<tr>
<td valign="top">

1292



</td>
<td valign="top">

ERR\_SQLSCRIPT\_ILLEGAL\_EXIT\_STMT



</td>
<td valign="top">

Illegal EXIT statement, it must appear inside a loop.



</td>
</tr>
<tr>
<td valign="top">

1293



</td>
<td valign="top">

ERR\_SQLSCRIPT\_ID\_EXCEPTION\_TYPE



</td>
<td valign="top">

The identifier name must be an exception name.



</td>
</tr>
<tr>
<td valign="top">

1294



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INTO\_CLAUSE



</td>
<td valign="top">

An INTO clause is expected in the SELECT statement.



</td>
</tr>
<tr>
<td valign="top">

1295



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ALLOWED\_STMT



</td>
<td valign="top">

The statement is not permitted.



</td>
</tr>
<tr>
<td valign="top">

1296



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_CURSOR



</td>
<td valign="top">

The identifier is not a cursor.



</td>
</tr>
<tr>
<td valign="top">

1297



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NUM\_FETCH\_VALUES



</td>
<td valign="top">

There is an incorrect number of values in the INTO list of a FETCH statement.



</td>
</tr>
<tr>
<td valign="top">

1298



</td>
<td valign="top">

ERR\_SQLSCRIPT\_UNHANDLED\_EXCEPTION



</td>
<td valign="top">

Unhandled user-defined exception.



</td>
</tr>
<tr>
<td valign="top">

1299



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NO\_DATA\_FOUND



</td>
<td valign="top">

No data found.



</td>
</tr>
<tr>
<td valign="top">

1300



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FETCH\_MANY\_ROWS



</td>
<td valign="top">

The fetch returned more than the requested number of rows.



</td>
</tr>
<tr>
<td valign="top">

1301



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VALUE\_ERROR



</td>
<td valign="top">

Numeric or value error.



</td>
</tr>
<tr>
<td valign="top">

1302



</td>
<td valign="top">

ERR\_SQLSCRIPT\_OUT\_PARAM\_IN\_FUNCTION



</td>
<td valign="top">

The parallelizable function cannot have an OUT or an IN OUT parameter.



</td>
</tr>
<tr>
<td valign="top">

1303



</td>
<td valign="top">

ERR\_SQLSCRIPT\_USER\_DEFINED\_EXCEPTION



</td>
<td valign="top">

User-defined exception.



</td>
</tr>
<tr>
<td valign="top">

1304



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CURSOR\_ALREADY\_OPEN



</td>
<td valign="top">

The cursor is already opened.



</td>
</tr>
<tr>
<td valign="top">

1305



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_RETURN\_TYPE



</td>
<td valign="top">

The return type is invalid.



</td>
</tr>
<tr>
<td valign="top">

1306



</td>
<td valign="top">

ERR\_SQLSCRIPT\_RETURN\_TYPE\_MISMATCH



</td>
<td valign="top">

Return type mismatch.



</td>
</tr>
<tr>
<td valign="top">

1307



</td>
<td valign="top">

ERR\_SQLSCRIPT\_UNSUPPORTED\_DATATYPE



</td>
<td valign="top">

An unsupported datatype is used.



</td>
</tr>
<tr>
<td valign="top">

1308



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_SINGLE\_ASSIGNMENT



</td>
<td valign="top">

Illegal single assignment.



</td>
</tr>
<tr>
<td valign="top">

1309



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_USE\_OF\_TABLE\_VARIABLE



</td>
<td valign="top">

Invalid use of a table variable.



</td>
</tr>
<tr>
<td valign="top">

1310



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ALLOWED\_SCALAR\_TYPE



</td>
<td valign="top">

A scalar type is not allowed.



</td>
</tr>
<tr>
<td valign="top">

1311



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NO\_OUT\_PARAM



</td>
<td valign="top">

The out parameter is not specified.



</td>
</tr>
<tr>
<td valign="top">

1312



</td>
<td valign="top">

ERR\_SQLSCRIPT\_AT\_MOST\_ONE\_OUT\_PARAM



</td>
<td valign="top">

At most one output parameter is allowed.



</td>
</tr>
<tr>
<td valign="top">

1313



</td>
<td valign="top">

ERR\_SQLSCRIPT\_OUT\_PARAM\_TABLE



</td>
<td valign="top">

The output parameter should be a table or a table variable.



</td>
</tr>
<tr>
<td valign="top">

1314



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_VARIABLE\_NAME



</td>
<td valign="top">

"inappropriate variable name: do not allow """" or '\_SYS\_' prefix for the name of variable or parameter"



</td>
</tr>
<tr>
<td valign="top">

1315



</td>
<td valign="top">

ERR\_SQLSCRIPT\_RETURN\_RESULT\_SET\_WITH\_RESULTVIEW



</td>
<td valign="top">

Return result set from SELECT statement exist when result view is defined



</td>
</tr>
<tr>
<td valign="top">

1316



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ASSIGNED\_OUT\_TABVAR



</td>
<td valign="top">

some out table variable is not assigned



</td>
</tr>
<tr>
<td valign="top">

1317



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_NAME\_MAX\_LEN



</td>
<td valign="top">

Function name exceeds max. limit



</td>
</tr>
<tr>
<td valign="top">

1318



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_NOT\_DEFINED



</td>
<td valign="top">

Built-in function not defined



</td>
</tr>
<tr>
<td valign="top">

1319



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_TABLE\_NAME



</td>
<td valign="top">

Parameter must be a table name



</td>
</tr>
<tr>
<td valign="top">

1320



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_ATTRIBUTE\_WITH\_SCHEMA



</td>
<td valign="top">

Parameter must be an attribute name without a table name upfront



</td>
</tr>
<tr>
<td valign="top">

1321



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_ATTRIBUTE\_WITH\_ALIAS



</td>
<td valign="top">

Parameter must be an attribute name without an alias



</td>
</tr>
<tr>
<td valign="top">

1322



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CALC\_ATTR\_NOT\_ALLOWED



</td>
<td valign="top">

CE\_CALC not allowed



</td>
</tr>
<tr>
<td valign="top">

1323



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_COL\_OR\_AGGR\_VECTOR



</td>
<td valign="top">

Parameter must be a vector of columns or aggregations



</td>
</tr>
<tr>
<td valign="top">

1324



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_MISSING\_JOIN\_ATTR\_IN\_PROJECTION



</td>
<td valign="top">

Join attribute must be available in projection list



</td>
</tr>
<tr>
<td valign="top">

1325



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_SQLIDENT\_VECTOR



</td>
<td valign="top">

Parameter must be a vector of sql identifiers



</td>
</tr>
<tr>
<td valign="top">

1326



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DUPLICATE\_ATTRIBUTE\_NAME



</td>
<td valign="top">

Duplicate attribute name



</td>
</tr>
<tr>
<td valign="top">

1327



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_UNSUPPORTED\_TYPE



</td>
<td valign="top">

Parameter has a non supported type



</td>
</tr>
<tr>
<td valign="top">

1328



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_MISSING\_ATTRIBUTE\_IN\_PROJECTION



</td>
<td valign="top">

Attribute not found in column table



</td>
</tr>
<tr>
<td valign="top">

1329



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_DUPLICATE\_COLUMN\_NAME



</td>
<td valign="top">

Duplicate column name



</td>
</tr>
<tr>
<td valign="top">

1330



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_CALCATTR\_EXPRESSION\_SYNTAX



</td>
<td valign="top">

Syntax Error for calculated Attribute



</td>
</tr>
<tr>
<td valign="top">

1331



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_FILTER\_EXPRESSION\_SYNTAX



</td>
<td valign="top">

Syntax Error in filter expression



</td>
</tr>
<tr>
<td valign="top">

1332



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_FIRST\_PARAM\_NOT\_COLUMN\_TABLE



</td>
<td valign="top">

Parameter must be a valid column table or projection view on column tables



</td>
</tr>
<tr>
<td valign="top">

1333



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_JOINATTR\_NOT\_FOUND\_IN\_VAR



</td>
<td valign="top">

Join attributes not found in variable



</td>
</tr>
<tr>
<td valign="top">

1334



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_IN\_PARAM\_NOT\_SAME\_TABLE\_TYPE



</td>
<td valign="top">

Input parameters do not have the same table type



</td>
</tr>
<tr>
<td valign="top">

1335



</td>
<td valign="top">

ERR\_SQLSCRIPT\_RUNTIME\_CYCLIC\_DEPENDENCY



</td>
<td valign="top">

Cyclic dependency found in a runtime procedure



</td>
</tr>
<tr>
<td valign="top">

1336



</td>
<td valign="top">

ERR\_SQLSCRIPT\_RUNTIME\_UNEXPECTED\_EXCEPTION



</td>
<td valign="top">

Unexpected internal exception caught in a runtime procedure



</td>
</tr>
<tr>
<td valign="top">

1337



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VAR\_DEPENDS\_ON\_UNASSIGNED\_VAR



</td>
<td valign="top">

Variable depends on an unassigned variable



</td>
</tr>
<tr>
<td valign="top">

1339



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TOO\_MANY\_PARAMS



</td>
<td valign="top">

Too many parameters



</td>
</tr>
<tr>
<td valign="top">

1340



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NESTED\_CALL\_TOO\_DEEP



</td>
<td valign="top">

The depth of the nested call is too deep



</td>
</tr>
<tr>
<td valign="top">

1341



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VERSION\_VALIDATION\_FAILED



</td>
<td valign="top">

Procedure version validation failed



</td>
</tr>
<tr>
<td valign="top">

1343



</td>
<td valign="top">

ERR\_SQLSCRIPT\_RETRY\_EXCEPTION



</td>
<td valign="top">

Retry Exception is occurred in a runtime procedure



</td>
</tr>
<tr>
<td valign="top">

1344



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ALLOWED\_DYNAMIC\_SQL



</td>
<td valign="top">

Dynamic SQL or DDL is not allowed



</td>
</tr>
<tr>
<td valign="top">

1345



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ALLOWED\_CONCURRENT\_WRITES



</td>
<td valign="top">

Concurrently two or more write operations to the same object are not allowed



</td>
</tr>
<tr>
<td valign="top">

1346



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ALLOWED\_CONCURRENT\_READ\_AND\_WRITE



</td>
<td valign="top">

Concurrently read and write operations to the same object are not allowed



</td>
</tr>
<tr>
<td valign="top">

1347



</td>
<td valign="top">

WRN\_SQLSCRIPT\_NOT\_RECOMMENDED\_FEATURE



</td>
<td valign="top">

Not recommended feature



</td>
</tr>
<tr>
<td valign="top">

1348



</td>
<td valign="top">

ERR\_SQLSCRIPT\_LLANG\_GET\_LIBRARY\_IMPORT\_LIST\_FAILED



</td>
<td valign="top">

Failed to retrieve the list of imported libraries from LLANG procedure



</td>
</tr>
<tr>
<td valign="top">

1349



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INITIAL\_ASSIGNMENT\_REQUIRED\_FOR\_CONSTANT\_TABLE



</td>
<td valign="top">

Assigning initial value is required for declaring constant table variable



</td>
</tr>
<tr>
<td valign="top">

1350



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_ALLOWED\_NON\_DETERMINISTIC\_FEATURE



</td>
<td valign="top">

Non-deterministic feature is not allowed



</td>
</tr>
<tr>
<td valign="top">

1351



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_PARSE\_TREE



</td>
<td valign="top">

Invalid parse tree



</td>
</tr>
<tr>
<td valign="top">

1352



</td>
<td valign="top">

ERR\_SQLSCRIPT\_ENCRYPTION\_NOT\_ALLOWED



</td>
<td valign="top">

Not allowed for encrypted procedure or function



</td>
</tr>
<tr>
<td valign="top">

1353



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NOT\_NULL\_COLUMN\_IGNORED



</td>
<td valign="top">

NOT NULL constraints in explicit table types are ignored



</td>
</tr>
<tr>
<td valign="top">

1354



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CURSOR\_NOT\_OPENED



</td>
<td valign="top">

Cursor to be fetched has not been opened yet



</td>
</tr>
<tr>
<td valign="top">

1355



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_EXTERN\_LANG



</td>
<td valign="top">

Invalid external language



</td>
</tr>
<tr>
<td valign="top">

1356



</td>
<td valign="top">

ERR\_SQLSCRIPT\_COMPOSITE



</td>
<td valign="top">

Composite error in SQLScript processing



</td>
</tr>
<tr>
<td valign="top">

1357



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CE\_TYPE\_MISMATCH



</td>
<td valign="top">

There is a datatype mismatch in the CE function.



</td>
</tr>
<tr>
<td valign="top">

1358



</td>
<td valign="top">

ERR\_SQLSCRIPT\_LIB\_WITHOUT\_USING



</td>
<td valign="top">

The USING statement is required before use.



</td>
</tr>
<tr>
<td valign="top">

1359



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TOO\_MANY\_MEMBERS



</td>
<td valign="top">

The expected library member count has been surpassed.



</td>
</tr>
<tr>
<td valign="top">

1360



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_INPUT



</td>
<td valign="top">

Invalid input.



</td>
</tr>
<tr>
<td valign="top">

1361



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_PRAGMA



</td>
<td valign="top">

Invalid pragma.



</td>
</tr>
<tr>
<td valign="top">

1362



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CALLSTACK\_TOO\_DEEP



</td>
<td valign="top">

The depth of the sqlscript callstack is too deep.



</td>
</tr>
<tr>
<td valign="top">

1776



</td>
<td valign="top">

ERR\_CONFIG\_UNSUPPORTED



</td>
<td valign="top">

Configuration error.



</td>
</tr>
<tr>
<td valign="top">

1777



</td>
<td valign="top">

WRN\_CONFIG\_UNSUPPORTED



</td>
<td valign="top">

Configuration warning.



</td>
</tr>
<tr>
<td valign="top">

1792



</td>
<td valign="top">

ERR\_SHM



</td>
<td valign="top">

shared memory error



</td>
</tr>
<tr>
<td valign="top">

1793



</td>
<td valign="top">

ERR\_SHM\_CREATE\_INVALID



</td>
<td valign="top">

invalid key or invalid size



</td>
</tr>
<tr>
<td valign="top">

1794



</td>
<td valign="top">

ERR\_SHM\_CREATE\_ALREADY\_EXIST



</td>
<td valign="top">

the segment already exists



</td>
</tr>
<tr>
<td valign="top">

1795



</td>
<td valign="top">

ERR\_SHM\_CREATE\_EXCEED\_LIMIT



</td>
<td valign="top">

exceed the system-wide limit on shared memory



</td>
</tr>
<tr>
<td valign="top">

1796



</td>
<td valign="top">

ERR\_SHM\_CREATE\_NOT\_EXIST



</td>
<td valign="top">

"no segment exists for the given key and IPC\_CREAT was not specified"



</td>
</tr>
<tr>
<td valign="top">

1797



</td>
<td valign="top">

ERR\_SHM\_CREATE\_NO\_ACCESS



</td>
<td valign="top">

the user does not have permission to access the shared memory segment



</td>
</tr>
<tr>
<td valign="top">

1798



</td>
<td valign="top">

ERR\_SHM\_CREATE\_NO\_MORE\_MEMORY



</td>
<td valign="top">

no memory could be allocated for segment overhead



</td>
</tr>
<tr>
<td valign="top">

1799



</td>
<td valign="top">

ERR\_SHM\_DROP\_INVALID



</td>
<td valign="top">

invalid shm id



</td>
</tr>
<tr>
<td valign="top">

1800



</td>
<td valign="top">

ERR\_SHM\_DROP\_NO\_ACCESS



</td>
<td valign="top">

allow read access for shm id



</td>
</tr>
<tr>
<td valign="top">

1801



</td>
<td valign="top">

ERR\_SHM\_DROP\_REMOVED\_IDENTIFIER



</td>
<td valign="top">

shm id points to a removed identifier



</td>
</tr>
<tr>
<td valign="top">

1802



</td>
<td valign="top">

ERR\_SHM\_DROP\_NO\_PERMISSION



</td>
<td valign="top">

the effective user ID of the calling process is not the creator



</td>
</tr>
<tr>
<td valign="top">

1803



</td>
<td valign="top">

ERR\_SHM\_DROP\_OVERFLOW



</td>
<td valign="top">

the gid or uid value is too large to be stored in the structure



</td>
</tr>
<tr>
<td valign="top">

1804



</td>
<td valign="top">

ERR\_SHM\_ATTACH\_NO\_ACCESS



</td>
<td valign="top">

the user does not have permission to access the shared memory segment



</td>
</tr>
<tr>
<td valign="top">

1805



</td>
<td valign="top">

ERR\_SHM\_ATTACH\_INVALID



</td>
<td valign="top">

invalid shm id



</td>
</tr>
<tr>
<td valign="top">

1806



</td>
<td valign="top">

ERR\_SHM\_ATTACH\_NO\_MORE\_MEMORY



</td>
<td valign="top">

no memory could be allocated for the descriptor or for the page tables



</td>
</tr>
<tr>
<td valign="top">

1807



</td>
<td valign="top">

ERR\_SHM\_UNKNOWN



</td>
<td valign="top">

unknown shared memory error



</td>
</tr>
<tr>
<td valign="top">

2048



</td>
<td valign="top">

ERR\_CS



</td>
<td valign="top">

column store error



</td>
</tr>
<tr>
<td valign="top">

2049



</td>
<td valign="top">

ERR\_CS\_NO\_PRIMARY\_KEY



</td>
<td valign="top">

primary key is not specified for column table



</td>
</tr>
<tr>
<td valign="top">

2050



</td>
<td valign="top">

ERR\_CS\_NOT\_SUPPORTED\_DDL



</td>
<td valign="top">

not supported DDL type for column table



</td>
</tr>
<tr>
<td valign="top">

2051



</td>
<td valign="top">

ERR\_CS\_NOT\_SUPPORTED\_DATA\_TYPE



</td>
<td valign="top">

not supported data type for column table



</td>
</tr>
<tr>
<td valign="top">

2052



</td>
<td valign="top">

ERR\_CS\_NOT\_SUPPORTED\_DML



</td>
<td valign="top">

not supported DML type for column table



</td>
</tr>
<tr>
<td valign="top">

2053



</td>
<td valign="top">

ERR\_CS\_INVALID\_RETURNED\_VALUE



</td>
<td valign="top">

invalid returned value from attribute engine



</td>
</tr>
<tr>
<td valign="top">

2054



</td>
<td valign="top">

ERR\_CS\_DELTA\_LOG\_REPLAY\_FAILED



</td>
<td valign="top">

The delta log replay failed.



</td>
</tr>
<tr>
<td valign="top">

2055



</td>
<td valign="top">

ERR\_CS\_MAXIMUM\_ROW



</td>
<td valign="top">

maximum number of rows per table or partition reached



</td>
</tr>
<tr>
<td valign="top">

2056



</td>
<td valign="top">

ERR\_CS\_CONSISTENCY\_CHECK\_FAILED



</td>
<td valign="top">

column store table consistency check failed



</td>
</tr>
<tr>
<td valign="top">

2304



</td>
<td valign="top">

ERR\_PYDBAPI



</td>
<td valign="top">

python dbapi error



</td>
</tr>
<tr>
<td valign="top">

2305



</td>
<td valign="top">

ERR\_PYDBAPI\_INTERFACE\_FAILURE



</td>
<td valign="top">

interface failure



</td>
</tr>
<tr>
<td valign="top">

2306



</td>
<td valign="top">

ERR\_PYDBAPI\_PROGRAMMING\_MISTAKE



</td>
<td valign="top">

programming mistake



</td>
</tr>
<tr>
<td valign="top">

2307



</td>
<td valign="top">

ERR\_PYDBAPI\_INVALID\_QUERY\_PARAMETER



</td>
<td valign="top">

invalid query parameter



</td>
</tr>
<tr>
<td valign="top">

2308



</td>
<td valign="top">

ERR\_PYDBAPI\_NOT\_SUPPORTED\_STR\_ENCODING



</td>
<td valign="top">

not supported encoding for string



</td>
</tr>
<tr>
<td valign="top">

2560



</td>
<td valign="top">

ERR\_METADATA



</td>
<td valign="top">

metadata error



</td>
</tr>
<tr>
<td valign="top">

2561



</td>
<td valign="top">

ERR\_DIST\_METADATA



</td>
<td valign="top">

distributed metadata error



</td>
</tr>
<tr>
<td valign="top">

2562



</td>
<td valign="top">

ERR\_DIST\_METADATA\_REDIRECT\_FAILURE



</td>
<td valign="top">

DDL redirect error



</td>
</tr>
<tr>
<td valign="top">

2563



</td>
<td valign="top">

ERR\_DIST\_METADATA\_DDL\_NOTIFICATION\_FAILURE



</td>
<td valign="top">

DDL notification error



</td>
</tr>
<tr>
<td valign="top">

2564



</td>
<td valign="top">

ERR\_DIST\_METADATA\_INVALID\_CONTAINER\_ID



</td>
<td valign="top">

DDL invalid container id



</td>
</tr>
<tr>
<td valign="top">

2565



</td>
<td valign="top">

ERR\_DIST\_METADATA\_INVALID\_INDEX\_ID



</td>
<td valign="top">

DDL invalid index id



</td>
</tr>
<tr>
<td valign="top">

2566



</td>
<td valign="top">

ERR\_DIST\_METADATA\_TNSCLIENT\_FAILURE



</td>
<td valign="top">

distributed environment error



</td>
</tr>
<tr>
<td valign="top">

2567



</td>
<td valign="top">

ERR\_DIST\_METADATA\_NETWORK\_FAILURE



</td>
<td valign="top">

network error



</td>
</tr>
<tr>
<td valign="top">

2568



</td>
<td valign="top">

ERR\_DIST\_METADATA\_NOT\_SUPPORT



</td>
<td valign="top">

metadata update not supported in secondary



</td>
</tr>
<tr>
<td valign="top">

2569



</td>
<td valign="top">

ERR\_DIST\_METADATA\_MASTER\_UPDATE\_FAILURE



</td>
<td valign="top">

metadata update in primary indexserver is failed



</td>
</tr>
<tr>
<td valign="top">

2570



</td>
<td valign="top">

ERR\_METADATA\_ROW\_PAGE\_INTEGRITY\_FAILURE



</td>
<td valign="top">

row page consistency check is failed



</td>
</tr>
<tr>
<td valign="top">

2571



</td>
<td valign="top">

ERR\_INTEGRITY\_BROKEN\_METADATA



</td>
<td valign="top">

integrity check detects broken metadata



</td>
</tr>
<tr>
<td valign="top">

2572



</td>
<td valign="top">

ERR\_INTEGRITY\_INCONSISTENCY



</td>
<td valign="top">

integrity check detects inconsistency



</td>
</tr>
<tr>
<td valign="top">

2573



</td>
<td valign="top">

ERR\_INTEGRITY\_ORPHANED



</td>
<td valign="top">

integrity check detects orphaned object



</td>
</tr>
<tr>
<td valign="top">

2574



</td>
<td valign="top">

ERR\_METADATA\_SEGMENT\_MIGRATION\_GENERAL



</td>
<td valign="top">

metadata segment migration pre-check error



</td>
</tr>
<tr>
<td valign="top">

2575



</td>
<td valign="top">

ERR\_METADATA\_SEGMENT\_MIGRATION\_FATAL



</td>
<td valign="top">

metadata segment migration internal error



</td>
</tr>
<tr>
<td valign="top">

2576



</td>
<td valign="top">

ERR\_CATALOG\_INVALID\_ADDRESS



</td>
<td valign="top">

"attempt to access metadata of an invalid address \(already deleted or corrupted etc.\)"



</td>
</tr>
<tr>
<td valign="top">

2577



</td>
<td valign="top">

ERR\_CATALOG\_NULL\_TERMINATION



</td>
<td valign="top">

catalog object has wrong null termination



</td>
</tr>
<tr>
<td valign="top">

2578



</td>
<td valign="top">

ERR\_CATALOG\_LOCATION\_ERROR



</td>
<td valign="top">

catalog object has wrong location



</td>
</tr>
<tr>
<td valign="top">

2579



</td>
<td valign="top">

ERR\_CATALOG\_INVALID\_REFERENCE



</td>
<td valign="top">

catalog object has invalid reference\(corrupted address\)



</td>
</tr>
<tr>
<td valign="top">

2580



</td>
<td valign="top">

ERR\_CATALOG\_UNEXPECTED\_REFERENCE



</td>
<td valign="top">

catalog object has wrong reference



</td>
</tr>
<tr>
<td valign="top">

2581



</td>
<td valign="top">

ERR\_CATALOG\_VALUE\_DOMAIN\_GENERAL



</td>
<td valign="top">

the value of catalog object is broken



</td>
</tr>
<tr>
<td valign="top">

2582



</td>
<td valign="top">

ERR\_CATALOG\_FOREIGN\_KEY\_CONSTRAINT



</td>
<td valign="top">

cannot find catalog object



</td>
</tr>
<tr>
<td valign="top">

2583



</td>
<td valign="top">

ERR\_CATALOG\_WRONG\_VAR\_SLOT\_SIZE



</td>
<td valign="top">

catalog object has wrong slot size



</td>
</tr>
<tr>
<td valign="top">

2584



</td>
<td valign="top">

ERR\_CATALOG\_CYCLIC\_DEPENDENCY



</td>
<td valign="top">

cannot make cyclic dependency



</td>
</tr>
<tr>
<td valign="top">

2585



</td>
<td valign="top">

ERR\_ES\_BROKEN\_METADATA



</td>
<td valign="top">

inconsistency between HANA and DT catalog



</td>
</tr>
<tr>
<td valign="top">

2586



</td>
<td valign="top">

ERR\_ES\_METADATA\_FIX\_FAIL



</td>
<td valign="top">

repair operation to fix inconsistency failed



</td>
</tr>
<tr>
<td valign="top">

2816



</td>
<td valign="top">

ERR\_SQLSCRIPT



</td>
<td valign="top">

SqlScript Error



</td>
</tr>
<tr>
<td valign="top">

2817



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_TOO\_MANY\_RETURN\_PARAM



</td>
<td valign="top">

SqlScript Built-in Function



</td>
</tr>
<tr>
<td valign="top">

2818



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_NOT\_FOUND



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2819



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TEMPLATE\_PARAMETER\_NUMBER\_WRONG



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2820



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VARIABLE\_NOT\_DECLARED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2821



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DUPLICATE\_VARIABLE\_NAME



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2822



</td>
<td valign="top">

ERR\_SQLSCRIPT\_SQL\_EXECUTION\_FAILED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2823



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DROP\_FUNCTION\_FAILED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2824



</td>
<td valign="top">

ERR\_SQLSCRIPT\_LOAD\_FUNCTION\_FAILED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2825



</td>
<td valign="top">

ERR\_SQLSCRIPT\_SIGNATURE\_MISMATCH\_WITH\_CATALOG



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2826



</td>
<td valign="top">

ERR\_SQLSCRIPT\_REGISTER\_FUNCTION\_IN\_CATALOG\_FAILED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2827



</td>
<td valign="top">

ERR\_SQLSCRIPT\_SCALAR\_INPUT\_PARAMS\_NOT\_SUPPORTED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2828



</td>
<td valign="top">

ERR\_SQLSCRIPT\_LANGUAGE\_NOT\_SUPPORTED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2829



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DROP\_FUNCTION\_FAILED\_EXISTING\_CALLER



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2830



</td>
<td valign="top">

ERR\_SQLSCRIPT\_LLANG\_EXACTLY\_ONE\_OUTPUT\_PARAM



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2831



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_FIRST\_PARAM\_NOT\_COLUMN\_TABLE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2832



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_COUNT\_NOT\_IN\_RANGE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2833



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_COUNT\_MISMATCH



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2834



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_INPUT



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2835



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_TABLE\_NAME



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2836



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_VARIABLE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2837



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_VARIABLE\_VECTOR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2838



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_SCALAR\_VALUE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2839



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_SQLIDENT\_VECTOR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2840



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_ATTRIBUTE\_WITH\_SCHEMA



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2841



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_MISSING\_ATTRIBUTE\_IN\_PROJECTION



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2842



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_MISSING\_JOIN\_ATTR\_IN\_PROJECTION



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2843



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TEMPL\_FUNCTION\_CAN\_NOT\_BE\_CALLED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2844



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_COUNT\_MISMATCH



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2845



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_WRONG\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2846



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_WRONG\_TYPE\_COMPARED\_TO\_SIGNATURE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2847



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_WRONG\_TABLE\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2848



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_MODE\_MISMATCH



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2849



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_UNSUPPORTED\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2850



</td>
<td valign="top">

ERR\_SQLSCRIPT\_NO\_OUTPUT\_PARAM



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2851



</td>
<td valign="top">

ERR\_SQLSCRIPT\_OUTPUT\_PARAM\_NOT\_TABLE\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2852



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_NOT\_DEFINED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2853



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VAR\_DEPENDS\_ON\_UNASSIGNED\_VAR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2854



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VAR\_CYCLIC\_DEPENDENCY



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2855



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_NOT\_INITIALIZED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2856



</td>
<td valign="top">

ERR\_SQLSCRIPT\_PARAM\_MISMATCH\_TABLE\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2857



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CALL\_OPEN\_MISSING\_CALL\_CLOSE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2858



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_IN\_PARAM\_NOT\_SAME\_TABLE\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2859



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_JOINATTR\_NOT\_FOUND\_IN\_VAR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2860



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_NOT\_NESTABLE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2861



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CALL\_CLOSE\_MISSING\_CALL\_OPEN



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2862



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TABLE\_TYPE\_NOT\_DERIVABLE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2863



</td>
<td valign="top">

ERR\_SQLSCRIPT\_MISSING\_FTC\_TYPE\_MAPPING



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2864



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INVALID\_TABLE\_TYPE\_NAME



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2865



</td>
<td valign="top">

ERR\_SQLSCRIPT\_DUPLICATE\_ATTRIBUTE\_NAME



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2866



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_EXISTING



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2867



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_TYPE\_NOT\_SUPPORTED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2868



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_NAME\_MAX\_LEN



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2869



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_ATTRIBUTE\_WITH\_ALIAS



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2870



</td>
<td valign="top">

ERR\_SQLSCRIPT\_INTERNAL\_ERR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2871



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_AGGREGFUN\_VECTOR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2872



</td>
<td valign="top">

ERR\_SQLSCRIPT\_FUNCTION\_NAME\_INVALID



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2873



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_PROJECTION\_VECTOR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2874



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_FILTER\_EXPRESSION



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2876



</td>
<td valign="top">

ERR\_SQLSCRIPT\_JSLANG\_EXACTLY\_ONE\_OUTPUT\_PARAM



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2877



</td>
<td valign="top">

ERR\_SQLSCRIPT\_SQLLANG\_EXACTLY\_ONE\_OUTPUT\_PARAM



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2878



</td>
<td valign="top">

ERR\_SQLSCRIPT\_GENERICLANG\_EXACTLY\_ONE\_OUTPUT\_PARAM



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2879



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_TABLE\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2880



</td>
<td valign="top">

ERR\_SQLSCRIPT\_VARIABLE\_NOT\_TABLE\_TYPE



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2881



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_CALCATTR\_EXPRESSION\_SYNTAX



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2882



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_UNEVEN\_NR\_OF\_PARAMS



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2883



</td>
<td valign="top">

ERR\_SQLSCRIPT\_CALC\_ATTR\_NOT\_ALLOWED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2884



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_DUPLICATE\_COLUMN\_NAME



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2885



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_KEY\_VALUE\_VECTOR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2886



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_CALCATTR\_REFERENCED\_FIELD\_MISSING



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2887



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_FILTER\_REFERENCED\_FIELD\_MISSING



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2888



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_FILTER\_EXPRESSION\_SYNTAX



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2889



</td>
<td valign="top">

ERR\_SQLSCRIPT\_BUILTIN\_PARAM\_NOT\_COL\_OR\_AGGR\_VECTOR



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2890



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TABLE\_INPUT\_PARAMS\_NOT\_SUPPORTED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

2891



</td>
<td valign="top">

ERR\_SQLSCRIPT\_TABLE\_INOUT\_PARAMS\_NOT\_SUPPORTED



</td>
<td valign="top">

SqlScript



</td>
</tr>
<tr>
<td valign="top">

3584



</td>
<td valign="top">

ERR\_DIST\_SQL



</td>
<td valign="top">

distributed SQL error



</td>
</tr>
<tr>
<td valign="top">

3585



</td>
<td valign="top">

ERR\_DIST\_SQL\_EXPR\_SHIPPING\_FAILURE



</td>
<td valign="top">

expression shipping failure



</td>
</tr>
<tr>
<td valign="top">

3586



</td>
<td valign="top">

ERR\_DIST\_SQL\_OPERATOR\_SHIPPING\_FAILURE



</td>
<td valign="top">

operator shipping failure



</td>
</tr>
<tr>
<td valign="top">

3587



</td>
<td valign="top">

ERR\_DIST\_SQL\_INVALID\_PROTOCOL



</td>
<td valign="top">

invalid protocol or service shutdown during distributed query execution



</td>
</tr>
<tr>
<td valign="top">

3588



</td>
<td valign="top">

ERR\_DIST\_SQL\_SEQUENCE\_SHIPPING\_FAILURE



</td>
<td valign="top">

sequence shipping failure



</td>
</tr>
<tr>
<td valign="top">

3589



</td>
<td valign="top">

ERR\_DIST\_SQL\_REMOTE\_EXECUTION\_FAILURE



</td>
<td valign="top">

remote query execution failure



</td>
</tr>
<tr>
<td valign="top">

3840



</td>
<td valign="top">

ERR\_AUDITING



</td>
<td valign="top">

general auditing error



</td>
</tr>
<tr>
<td valign="top">

3841



</td>
<td valign="top">

ERR\_AUDITING\_NO\_PRIV\_NAME



</td>
<td valign="top">

Invalid privilege



</td>
</tr>
<tr>
<td valign="top">

3842



</td>
<td valign="top">

ERR\_AUDITING\_TRAIL\_WRITER\_BLOCKED



</td>
<td valign="top">

Audit trail writer is blocked



</td>
</tr>
<tr>
<td valign="top">

3843



</td>
<td valign="top">

ERR\_AUDITING\_POLICY\_ALREADY\_EXISTS



</td>
<td valign="top">

Audit policy with current name already exists



</td>
</tr>
<tr>
<td valign="top">

3844



</td>
<td valign="top">

ERR\_AUDITING\_INV\_POLICY\_TYPE



</td>
<td valign="top">

Invalid combination of audit actions



</td>
</tr>
<tr>
<td valign="top">

3845



</td>
<td valign="top">

ERR\_AUDITING\_INV\_ACTION\_STATUS



</td>
<td valign="top">

Invalid action status for auditing



</td>
</tr>
<tr>
<td valign="top">

3846



</td>
<td valign="top">

ERR\_AUDITING\_INV\_LEVEL



</td>
<td valign="top">

Invalid auditing level



</td>
</tr>
<tr>
<td valign="top">

3847



</td>
<td valign="top">

ERR\_AUDITING\_INV\_POLICY\_NAME



</td>
<td valign="top">

Invalid policy name



</td>
</tr>
<tr>
<td valign="top">

3848



</td>
<td valign="top">

ERR\_AUDITING\_INV\_ACTION\_OBJECT\_TYPE



</td>
<td valign="top">

Invalid combination of audit action and object type



</td>
</tr>
<tr>
<td valign="top">

3849



</td>
<td valign="top">

ERR\_AUDITING\_INV\_OBJECT\_TYPE



</td>
<td valign="top">

Audit policy for this object type not supported



</td>
</tr>
<tr>
<td valign="top">

3850



</td>
<td valign="top">

ERR\_AUDITING\_INV\_ACTION



</td>
<td valign="top">

Invalid action for tenant specific audit policy.



</td>
</tr>
<tr>
<td valign="top">

3851



</td>
<td valign="top">

ERR\_AUDITING\_INV\_RETENTION



</td>
<td valign="top">

Number of days for retention too small or no retention for used trail types allowed at all.



</td>
</tr>
<tr>
<td valign="top">

4096



</td>
<td valign="top">

ERR\_PLANVIZ\_GENERAL



</td>
<td valign="top">

\[PlanViz\] general error



</td>
</tr>
<tr>
<td valign="top">

4097



</td>
<td valign="top">

ERR\_PLANVIZ\_PIN\_GENERAL



</td>
<td valign="top">

\[PlanViz\] invalid pin request



</td>
</tr>
<tr>
<td valign="top">

4098



</td>
<td valign="top">

ERR\_PLANVIZ\_INVALID\_PLAN\_GENERAL



</td>
<td valign="top">

\[PlanViz\] invalid plan



</td>
</tr>
<tr>
<td valign="top">

4099



</td>
<td valign="top">

ERR\_PLANVIZ\_PLAN\_CACHE\_GENERAL



</td>
<td valign="top">

\[PlanViz\] plan cache error



</td>
</tr>
<tr>
<td valign="top">

4100



</td>
<td valign="top">

ERR\_PLANVIZ\_NO\_PVPARAM



</td>
<td valign="top">

\[PlanViz\] PlanVizParam does not exist



</td>
</tr>
<tr>
<td valign="top">

4101



</td>
<td valign="top">

ERR\_PLANVIZ\_PROC\_LANG\_SUPPORT



</td>
<td valign="top">

\[PlanViz\] procedure language not supported



</td>
</tr>
<tr>
<td valign="top">

4102



</td>
<td valign="top">

ERR\_PLANVIZ\_MARK\_MIN\_COST\_PLAN



</td>
<td valign="top">

\[PlanViz\] cannot mark min-cost plan



</td>
</tr>
<tr>
<td valign="top">

4103



</td>
<td valign="top">

ERR\_PLANVIZ\_PARSE\_TREE\_NOT\_FOUND



</td>
<td valign="top">

\[PlanViz\] parse tree not found



</td>
</tr>
<tr>
<td valign="top">

4104



</td>
<td valign="top">

ERR\_PLANVIZ\_PLAN\_NOT\_FOUND



</td>
<td valign="top">

\[PlanViz\] plan not found



</td>
</tr>
<tr>
<td valign="top">

4105



</td>
<td valign="top">

ERR\_PLANVIZ\_UNSUPPORTED\_STMT\_TYPE



</td>
<td valign="top">

\[PlanViz\] unsupported statement type



</td>
</tr>
<tr>
<td valign="top">

4106



</td>
<td valign="top">

ERR\_PLANVIZ\_REMOTE\_EXEC\_STATS



</td>
<td valign="top">

\[PlanViz\] error while gathering remote execution stats



</td>
</tr>
<tr>
<td valign="top">

4107



</td>
<td valign="top">

ERR\_PLANVIZ\_ENV\_NO\_STATS\_COLLECTOR



</td>
<td valign="top">

\[PlanViz\] exec stats collector not found



</td>
</tr>
<tr>
<td valign="top">

4108



</td>
<td valign="top">

ERR\_PLANVIZ\_EXPLAIN\_PLAN\_GENERAL



</td>
<td valign="top">

\[PlanViz\] explain plan failed



</td>
</tr>
<tr>
<td valign="top">

4109



</td>
<td valign="top">

ERR\_PLANVIZ\_TRACE\_ONLY\_GENERAL



</td>
<td valign="top">

\[PlanViz\] error in trace-only mode



</td>
</tr>
<tr>
<td valign="top">

4110



</td>
<td valign="top">

ERR\_PLANVIZ\_PLAN\_TRACE\_GENERAL



</td>
<td valign="top">

\[PlanViz\] error in Plan Trace



</td>
</tr>
<tr>
<td valign="top">

4161



</td>
<td valign="top">

ERR\_REORG\_GENERAL



</td>
<td valign="top">

Failed to execute reorganization



</td>
</tr>
<tr>
<td valign="top">

4162



</td>
<td valign="top">

ERR\_REORG\_TRANS\_BLOCKED\_GENERAL



</td>
<td valign="top">

Transaction blocked since runtime reorganization is in progress



</td>
</tr>
<tr>
<td valign="top">

4163



</td>
<td valign="top">

ERR\_REORG\_TRANS\_EXISTS\_GENERAL



</td>
<td valign="top">

Cannot start reorganization due to the transactions in execution



</td>
</tr>
<tr>
<td valign="top">

4192



</td>
<td valign="top">

ERR\_LDAP



</td>
<td valign="top">

General LDAP error.



</td>
</tr>
<tr>
<td valign="top">

4193



</td>
<td valign="top">

ERR\_LDAP\_CANNOT\_AUTHORIZE\_LOCALLY



</td>
<td valign="top">

Local authorization not allowed.



</td>
</tr>
<tr>
<td valign="top">

4194



</td>
<td valign="top">

ERR\_LDAP\_CANNOT\_CHANGE\_AUTHORIZATION\_MODE



</td>
<td valign="top">

Authorization mode change not allowed.



</td>
</tr>
<tr>
<td valign="top">

4195



</td>
<td valign="top">

ERR\_LDAP\_MAPPING\_ALREADY\_EXISTS



</td>
<td valign="top">

Role to LDAP group mapping already exists.



</td>
</tr>
<tr>
<td valign="top">

4196



</td>
<td valign="top">

ERR\_LDAP\_MAPPING\_DOESNT\_EXIST



</td>
<td valign="top">

Role to LDAP group mapping does not exist.



</td>
</tr>
<tr>
<td valign="top">

4197



</td>
<td valign="top">

ERR\_LDAP\_PROVIDER\_CREATION\_FAILED



</td>
<td valign="top">

Creating LDAP provider failed because of internal error.



</td>
</tr>
<tr>
<td valign="top">

4198



</td>
<td valign="top">

ERR\_LDAP\_PROVIDER\_DELETION\_FAILED



</td>
<td valign="top">

Deleting LDAP provider failed because of internal error.



</td>
</tr>
<tr>
<td valign="top">

4199



</td>
<td valign="top">

ERR\_LDAP\_PROVIDER\_ALTER\_FAILED



</td>
<td valign="top">

Alter LDAP provider failed because of internal error.



</td>
</tr>
<tr>
<td valign="top">

4200



</td>
<td valign="top">

ERR\_LDAP\_PROVIDER\_VALIDATE\_FAILED



</td>
<td valign="top">

Validate LDAP provider failed because of internal error.



</td>
</tr>
<tr>
<td valign="top">

4201



</td>
<td valign="top">

ERR\_LDAP\_PROVIDER\_ALREADY\_EXISTS



</td>
<td valign="top">

LDAP provider already exists.



</td>
</tr>
<tr>
<td valign="top">

4202



</td>
<td valign="top">

ERR\_LDAP\_INVALID\_PROVIDER\_NAME



</td>
<td valign="top">

Invalid LDAP provider name.



</td>
</tr>
<tr>
<td valign="top">

4203



</td>
<td valign="top">

ERR\_LDAP\_MALFORMED\_CREDENTIALS



</td>
<td valign="top">

Credentials not provided in proper format.



</td>
</tr>
<tr>
<td valign="top">

4204



</td>
<td valign="top">

ERR\_LDAP\_PASSWORD\_MUTUAL\_EXCLUSION\_FAILED



</td>
<td valign="top">

Local password authentication and LDAP authentication cannot be enabled together for the same user.



</td>
</tr>
<tr>
<td valign="top">

4225



</td>
<td valign="top">

ERR\_PROVIDER



</td>
<td valign="top">

General provider error



</td>
</tr>
<tr>
<td valign="top">

4226



</td>
<td valign="top">

ERR\_PROVIDER\_INV\_SUBJECT\_NAME



</td>
<td valign="top">

Invalid subject name layout



</td>
</tr>
<tr>
<td valign="top">

4227



</td>
<td valign="top">

ERR\_PROVIDER\_INV\_ISSUER\_NAME



</td>
<td valign="top">

Invalid issuer name layout



</td>
</tr>
<tr>
<td valign="top">

4228



</td>
<td valign="top">

ERR\_PROVIDER\_ALREADY\_EXISTS



</td>
<td valign="top">

Provider already exists



</td>
</tr>
<tr>
<td valign="top">

4229



</td>
<td valign="top">

ERR\_PROVIDER\_INVALID\_PROVIDER\_NAME



</td>
<td valign="top">

Invalid provider name



</td>
</tr>
<tr>
<td valign="top">

4230



</td>
<td valign="top">

ERR\_PROVIDER\_INVALID\_ASSERTION



</td>
<td valign="top">

Invalid assertion



</td>
</tr>
<tr>
<td valign="top">

4231



</td>
<td valign="top">

ERR\_PROVIDER\_INVALID\_MAPPED\_USER\_NAME



</td>
<td valign="top">

Invalid or empty mapped user name



</td>
</tr>
<tr>
<td valign="top">

4232



</td>
<td valign="top">

ERR\_PROVIDER\_ADDING\_USER\_MAPPING\_FAILED



</td>
<td valign="top">

Adding a new provider user mapping failed



</td>
</tr>
<tr>
<td valign="top">

4233



</td>
<td valign="top">

ERR\_PROVIDER\_CREATION\_FAILED



</td>
<td valign="top">

Creating provider failed because of internal error:



</td>
</tr>
<tr>
<td valign="top">

4234



</td>
<td valign="top">

ERR\_PROVIDER\_DELETION\_FAILED



</td>
<td valign="top">

Deleting provider failed because of internal error:



</td>
</tr>
<tr>
<td valign="top">

4235



</td>
<td valign="top">

ERR\_PROVIDER\_ALTER\_FAILED



</td>
<td valign="top">

Alter provider failed because of internal error:



</td>
</tr>
<tr>
<td valign="top">

4236



</td>
<td valign="top">

ERR\_PROVIDER\_DUPLICATE\_ENTITY



</td>
<td valign="top">

EntityID already exists



</td>
</tr>
<tr>
<td valign="top">

4237



</td>
<td valign="top">

ERR\_PROVIDER\_INVALID\_ENTITY



</td>
<td valign="top">

Invalid entity id



</td>
</tr>
<tr>
<td valign="top">

4238



</td>
<td valign="top">

ERR\_PROVIDER\_DUPLICATE\_ISSUER



</td>
<td valign="top">

Duplicate Provider for this issuer



</td>
</tr>
<tr>
<td valign="top">

4239



</td>
<td valign="top">

ERR\_PROVIDER\_INVALID\_CLAIM



</td>
<td valign="top">

Invalid claim



</td>
</tr>
<tr>
<td valign="top">

4240



</td>
<td valign="top">

ERR\_PROVIDER\_DUPLICATE\_IDENTITY



</td>
<td valign="top">

Duplicate identity for this provider.



</td>
</tr>
<tr>
<td valign="top">

4248



</td>
<td valign="top">

ERR\_USER\_PARAMETERS



</td>
<td valign="top">

general user parameter error



</td>
</tr>
<tr>
<td valign="top">

4249



</td>
<td valign="top">

ERR\_USER\_PARAM\_DUPLICATE\_EMAIL\_ADDRESS



</td>
<td valign="top">

Same email address cannot be used for different users



</td>
</tr>
<tr>
<td valign="top">

4250



</td>
<td valign="top">

ERR\_USER\_PARAM\_PRIORITY\_OUT\_OF\_RANGE



</td>
<td valign="top">

Priority out of range



</td>
</tr>
<tr>
<td valign="top">

4251



</td>
<td valign="top">

ERR\_USER\_PARAM\_INVALID\_STATEMENT\_MEMORY\_LIMIT



</td>
<td valign="top">

Invalid statement memory limit



</td>
</tr>
<tr>
<td valign="top">

4252



</td>
<td valign="top">

ERR\_USER\_PARAM\_INVALID\_STATEMENT\_THREAD\_LIMIT



</td>
<td valign="top">

Invalid statement thread limit



</td>
</tr>
<tr>
<td valign="top">

4253



</td>
<td valign="top">

ERR\_USER\_PARAM\_INVALID\_PARAMETER



</td>
<td valign="top">

Invalid parameter name



</td>
</tr>
<tr>
<td valign="top">

4273



</td>
<td valign="top">

ERR\_KERBEROS



</td>
<td valign="top">

general Kerberos error



</td>
</tr>
<tr>
<td valign="top">

4274



</td>
<td valign="top">

ERR\_KERBEROS\_DUPLICATE\_PROVIDER



</td>
<td valign="top">

Duplicate specification of identity for KERBEROS



</td>
</tr>
<tr>
<td valign="top">

4275



</td>
<td valign="top">

ERR\_KERBEROS\_MISSING\_PROVIDER



</td>
<td valign="top">

Missing specification of identity for KERBEROS



</td>
</tr>
<tr>
<td valign="top">

4280



</td>
<td valign="top">

ERR\_TICKET



</td>
<td valign="top">

general ticket error



</td>
</tr>
<tr>
<td valign="top">

4281



</td>
<td valign="top">

ERR\_TICKET\_DUPLICATE



</td>
<td valign="top">

Duplicate specification of identity for this kind of SAP ticket



</td>
</tr>
<tr>
<td valign="top">

4282



</td>
<td valign="top">

ERR\_TICKET\_MISSING\_PROVIDER



</td>
<td valign="top">

Missing specification of identity for this kind of SAP ticket



</td>
</tr>
<tr>
<td valign="top">

4289



</td>
<td valign="top">

ERR\_X509



</td>
<td valign="top">

general X.509 error



</td>
</tr>
<tr>
<td valign="top">

4290



</td>
<td valign="top">

ERR\_X509\_DUPLICATE\_SUBJECT\_ISSUER



</td>
<td valign="top">

Duplicate specification of subject and issuer for X509



</td>
</tr>
<tr>
<td valign="top">

4291



</td>
<td valign="top">

ERR\_X509\_UNKNOWN\_SUBJECT\_ISSUER



</td>
<td valign="top">

Unknown specification of subject and issuer for this user



</td>
</tr>
<tr>
<td valign="top">

4292



</td>
<td valign="top">

ERR\_X509\_INV\_SUBJECT\_NAME



</td>
<td valign="top">

Invalid subject name layout



</td>
</tr>
<tr>
<td valign="top">

4293



</td>
<td valign="top">

ERR\_X509\_INV\_ISSUER\_NAME



</td>
<td valign="top">

Invalid issuer name layout



</td>
</tr>
<tr>
<td valign="top">

4320



</td>
<td valign="top">

ERR\_SSL



</td>
<td valign="top">

general SSL error



</td>
</tr>
<tr>
<td valign="top">

4321



</td>
<td valign="top">

ERR\_SSL\_ENFORCE



</td>
<td valign="top">

only secure connections are allowed



</td>
</tr>
<tr>
<td valign="top">

4336



</td>
<td valign="top">

ERR\_USER\_REMOTE



</td>
<td valign="top">

general remote user error



</td>
</tr>
<tr>
<td valign="top">

4337



</td>
<td valign="top">

ERR\_USER\_REMOTE\_EXISTS



</td>
<td valign="top">

remote user mapping already exists



</td>
</tr>
<tr>
<td valign="top">

4338



</td>
<td valign="top">

ERR\_USER\_REMOTE\_NOT\_EXISTS



</td>
<td valign="top">

remote user mapping does not exist



</td>
</tr>
<tr>
<td valign="top">

4640



</td>
<td valign="top">

ERR\_RS\_TABLE\_LOAD\_GENERAL



</td>
<td valign="top">

failed to load row table



</td>
</tr>
<tr>
<td valign="top">

4641



</td>
<td valign="top">

ERR\_RS\_TABLE\_LOAD\_WAIT\_TIMEOUT



</td>
<td valign="top">

waiting timeout for loading row table occurred



</td>
</tr>
<tr>
<td valign="top">

4642



</td>
<td valign="top">

ERR\_RS\_TABLE\_POST\_DROP



</td>
<td valign="top">

failed to delete row table data



</td>
</tr>
<tr>
<td valign="top">

4672



</td>
<td valign="top">

ERR\_DATAPROV



</td>
<td valign="top">

General Unified Data Provisioning error



</td>
</tr>
<tr>
<td valign="top">

4673



</td>
<td valign="top">

ERR\_DATAPROV\_DATASOURCE\_DOES\_NOT\_EXIST



</td>
<td valign="top">

Data source does not exist



</td>
</tr>
<tr>
<td valign="top">

4674



</td>
<td valign="top">

ERR\_DATAPROV\_INVALID\_LOGICAL\_DATASOURCE\_NAME



</td>
<td valign="top">

Invalid logical data source name



</td>
</tr>
<tr>
<td valign="top">

4675



</td>
<td valign="top">

ERR\_DATAPROV\_INVALID\_DATAFLOW\_PACKAGE\_NAME



</td>
<td valign="top">

Invalid dataflow package name



</td>
</tr>
<tr>
<td valign="top">

4676



</td>
<td valign="top">

ERR\_DATAPROV\_INVALID\_DATAFLOW\_OBJECT\_NAME



</td>
<td valign="top">

Invalid data flow object name



</td>
</tr>
<tr>
<td valign="top">

4677



</td>
<td valign="top">

ERR\_DATAPROV\_DATAFLOW\_DOES\_NOT\_EXIST



</td>
<td valign="top">

Data flow does not exist



</td>
</tr>
<tr>
<td valign="top">

4678



</td>
<td valign="top">

ERR\_DATAPROV\_INVALID\_DATAFLOW



</td>
<td valign="top">

Invalid data flow



</td>
</tr>
<tr>
<td valign="top">

4679



</td>
<td valign="top">

ERR\_DATAPROV\_INVALID\_DATASOURCE



</td>
<td valign="top">

Invalid data source



</td>
</tr>
<tr>
<td valign="top">

4680



</td>
<td valign="top">

ERR\_DATAPROV\_COULD\_NOT\_GENERATE\_JOB\_ID



</td>
<td valign="top">

Could not generate job ID



</td>
</tr>
<tr>
<td valign="top">

4704



</td>
<td valign="top">

ERR\_DPSERVER



</td>
<td valign="top">

General dpserver error occurred



</td>
</tr>
<tr>
<td valign="top">

4705



</td>
<td valign="top">

ERR\_DPSERVER\_SCHEMA\_CHANGE



</td>
<td valign="top">

Schema of table changed



</td>
</tr>
<tr>
<td valign="top">

4706



</td>
<td valign="top">

ERR\_DPSERVER\_SCHEMA\_CHANGE\_ON\_DATASOURCE



</td>
<td valign="top">

Schema of table changed in the remote source



</td>
</tr>
<tr>
<td valign="top">

4707



</td>
<td valign="top">

ERR\_DPSERVER\_TRUNCATE\_TABLE\_EVENT



</td>
<td valign="top">

Table truncated in the remote source



</td>
</tr>
<tr>
<td valign="top">

4708



</td>
<td valign="top">

ERR\_DPSERVER\_ADAPTER\_FAILURE



</td>
<td valign="top">

Adapter failure occurred on remote source



</td>
</tr>
<tr>
<td valign="top">

4709



</td>
<td valign="top">

ERR\_DPSERVER\_RECEIVER\_FAILURE



</td>
<td valign="top">

Receiver failure occurred on remote source



</td>
</tr>
<tr>
<td valign="top">

4710



</td>
<td valign="top">

ERR\_DPSERVER\_DISTRIBUTOR\_FAILURE



</td>
<td valign="top">

Distributor failure occurred on remote source



</td>
</tr>
<tr>
<td valign="top">

4711



</td>
<td valign="top">

ERR\_DPSERVER\_ADAPTER\_REMOTE\_SOURCE\_DOWN



</td>
<td valign="top">

Adapter failure remote source is down.



</td>
</tr>
<tr>
<td valign="top">

4712



</td>
<td valign="top">

ERR\_DPSERVER\_OPERATION\_NOT\_PERMITTED



</td>
<td valign="top">

Operation is not permitted



</td>
</tr>
<tr>
<td valign="top">

4713



</td>
<td valign="top">

ERR\_DPSERVER\_SCHEMA\_CHANGE\_ON\_DATASOURCE\_DROPTABLE\_OPERATION



</td>
<td valign="top">

Source table dropped in the remote source.



</td>
</tr>
<tr>
<td valign="top">

4736



</td>
<td valign="top">

ERR\_SCHEDULER\_JOB\_INVALID



</td>
<td valign="top">

Invalid scheduler job name.



</td>
</tr>
<tr>
<td valign="top">

4737



</td>
<td valign="top">

ERR\_SCHEDULER\_JOB\_EXISTS



</td>
<td valign="top">

Cannot use duplicate scheduler job name.



</td>
</tr>
<tr>
<td valign="top">

4864



</td>
<td valign="top">

ERR\_GEM



</td>
<td valign="top">

General GEM error



</td>
</tr>
<tr>
<td valign="top">

4865



</td>
<td valign="top">

ERR\_GEM\_WORKSPACE\_NOT\_EXISTS



</td>
<td valign="top">

GEM workspace does not exist



</td>
</tr>
<tr>
<td valign="top">

4866



</td>
<td valign="top">

ERR\_GEM\_WORKSPACE\_SCHEMA\_NOT\_EXISTS



</td>
<td valign="top">

Schema specified for GEM workspace does not exist



</td>
</tr>
<tr>
<td valign="top">

4867



</td>
<td valign="top">

ERR\_GEM\_WORKSPACE\_ALREADY\_EXISTS



</td>
<td valign="top">

GEM workspace already exists



</td>
</tr>
<tr>
<td valign="top">

4868



</td>
<td valign="top">

ERR\_GEM\_WORKSPACE\_URI\_TOO\_LONG



</td>
<td valign="top">

Workspace URI exceeds maximum allowed length



</td>
</tr>
<tr>
<td valign="top">

4869



</td>
<td valign="top">

ERR\_GEM\_ADD\_COLUMN



</td>
<td valign="top">

Failed to add column



</td>
</tr>
<tr>
<td valign="top">

4870



</td>
<td valign="top">

ERR\_GEM\_PREP\_INSERT



</td>
<td valign="top">

Failed in preparation to add column



</td>
</tr>
<tr>
<td valign="top">

4871



</td>
<td valign="top">

ERR\_GEM\_CALC



</td>
<td valign="top">

Calculation Scenario



</td>
</tr>
<tr>
<td valign="top">

4872



</td>
<td valign="top">

ERR\_GEM\_VISITOR



</td>
<td valign="top">

GEM Visitor



</td>
</tr>
<tr>
<td valign="top">

4873



</td>
<td valign="top">

ERR\_GEM\_GRAMMAR



</td>
<td valign="top">

GEM Grammar



</td>
</tr>
<tr>
<td valign="top">

4874



</td>
<td valign="top">

ERR\_GEM\_TREE\_BUILDER



</td>
<td valign="top">

Tree Builder



</td>
</tr>
<tr>
<td valign="top">

4875



</td>
<td valign="top">

ERR\_GEM\_TECHTYPE\_UNKNOWN



</td>
<td valign="top">

Techtype unknown in predicate/expression



</td>
</tr>
<tr>
<td valign="top">

4876



</td>
<td valign="top">

ERR\_GEM\_TECHTYPE\_MISMATCH



</td>
<td valign="top">

Mismatch of technical types



</td>
</tr>
<tr>
<td valign="top">

4877



</td>
<td valign="top">

ERR\_GEM\_TERM\_NOT\_EXISTS



</td>
<td valign="top">

Term does not exist



</td>
</tr>
<tr>
<td valign="top">

4878



</td>
<td valign="top">

ERR\_GEM\_TERM\_ALREADY\_EXISTS



</td>
<td valign="top">

Term already exists



</td>
</tr>
<tr>
<td valign="top">

4879



</td>
<td valign="top">

ERR\_GEM\_VERTEX\_NOT\_EXISTS



</td>
<td valign="top">

Vertex does not exist



</td>
</tr>
<tr>
<td valign="top">

4880



</td>
<td valign="top">

ERR\_GEM\_VERTEX\_ALREADY\_EXISTS



</td>
<td valign="top">

Vertex already exists



</td>
</tr>
<tr>
<td valign="top">

4881



</td>
<td valign="top">

ERR\_GEM\_LOCAL\_NAME\_NOT\_FOUND



</td>
<td valign="top">

Local name was not found



</td>
</tr>
<tr>
<td valign="top">

4882



</td>
<td valign="top">

ERR\_GEM\_LOCAL\_NAME\_ALREADY\_EXISTS



</td>
<td valign="top">

Local name already exists



</td>
</tr>
<tr>
<td valign="top">

4883



</td>
<td valign="top">

ERR\_GEM\_UNKNOWN\_FUNC



</td>
<td valign="top">

Unknown function



</td>
</tr>
<tr>
<td valign="top">

4884



</td>
<td valign="top">

ERR\_GEM\_FEATURE\_NOT\_SUPPORTED



</td>
<td valign="top">

This GEM feature is not supported



</td>
</tr>
<tr>
<td valign="top">

4885



</td>
<td valign="top">

ERR\_GEM\_FUNCTION



</td>
<td valign="top">

Error in using GEM function



</td>
</tr>
<tr>
<td valign="top">

4886



</td>
<td valign="top">

ERR\_GEM\_TECHTYPE\_MISSING



</td>
<td valign="top">

Techtype not specified



</td>
</tr>
<tr>
<td valign="top">

4887



</td>
<td valign="top">

ERR\_GEM\_URI\_MISSING



</td>
<td valign="top">

URI is missing



</td>
</tr>
<tr>
<td valign="top">

4888



</td>
<td valign="top">

ERR\_GEM\_TECHTYPE\_ERROR



</td>
<td valign="top">

GEM technical type error



</td>
</tr>
<tr>
<td valign="top">

5633



</td>
<td valign="top">

ERR\_CERTADM\_UNKNOWN



</td>
<td valign="top">

Unknown certificate administration error occurred



</td>
</tr>
<tr>
<td valign="top">

5634



</td>
<td valign="top">

ERR\_CERTADM\_INVALID\_CERT\_DEFINITION



</td>
<td valign="top">

Certificate definition inconsistent



</td>
</tr>
<tr>
<td valign="top">

5635



</td>
<td valign="top">

ERR\_CERTADM\_EXST\_CERTIFICATE



</td>
<td valign="top">

Certificate with same hash already exists



</td>
</tr>
<tr>
<td valign="top">

5636



</td>
<td valign="top">

ERR\_CERTADM\_NON\_EXST\_CERTIFICATE



</td>
<td valign="top">

Certificate could not be found in certificate store



</td>
</tr>
<tr>
<td valign="top">

5637



</td>
<td valign="top">

ERR\_CERTADM\_CERTIFICATE\_IN\_USE



</td>
<td valign="top">

Certificate could not be dropped because it is still in use by at least one PSE



</td>
</tr>
<tr>
<td valign="top">

5638



</td>
<td valign="top">

ERR\_CERTADM\_EXST\_PSE



</td>
<td valign="top">

PSE with same name already exists



</td>
</tr>
<tr>
<td valign="top">

5639



</td>
<td valign="top">

ERR\_CERTADM\_NON\_EXST\_PSE



</td>
<td valign="top">

PSE could not be found



</td>
</tr>
<tr>
<td valign="top">

5640



</td>
<td valign="top">

ERR\_CERTADM\_INVALID\_PURPOSE



</td>
<td valign="top">

Invalid purpose for PSE



</td>
</tr>
<tr>
<td valign="top">

5641



</td>
<td valign="top">

ERR\_CERTADM\_NO\_SUCH\_CERTIFICATE\_IN\_PSE



</td>
<td valign="top">

PSE does not contain such certificate



</td>
</tr>
<tr>
<td valign="top">

5642



</td>
<td valign="top">

ERR\_CERTADM\_PSE\_WITH\_DIFFERENT\_PURPOSE



</td>
<td valign="top">

PSE is already set to a different purpose



</td>
</tr>
<tr>
<td valign="top">

5643



</td>
<td valign="top">

ERR\_CERTADM\_INVALID\_PRIVATE\_KEY



</td>
<td valign="top">

Private key provided with own certificate is missing or invalid



</td>
</tr>
<tr>
<td valign="top">

5644



</td>
<td valign="top">

ERR\_CERTADM\_NO\_CERT\_FOR\_PRIVATE\_KEY



</td>
<td valign="top">

No certificate found for provided key



</td>
</tr>
<tr>
<td valign="top">

5645



</td>
<td valign="top">

ERR\_CERTADM\_INCOMPLETE\_CHAIN



</td>
<td valign="top">

Incomplete certificate chain



</td>
</tr>
<tr>
<td valign="top">

5646



</td>
<td valign="top">

ERR\_CERTADM\_INVALID\_CHAIN



</td>
<td valign="top">

Invalid certificate chain



</td>
</tr>
<tr>
<td valign="top">

5647



</td>
<td valign="top">

ERR\_CERTADM\_DANGLING\_CERTIFICATES



</td>
<td valign="top">

Invalid certificate chain: dangling certificates in PEM



</td>
</tr>
<tr>
<td valign="top">

5648



</td>
<td valign="top">

ERR\_CERTADM\_PSE\_WITH\_NO\_PURPOSE



</td>
<td valign="top">

PSE is not set to any purpose



</td>
</tr>
<tr>
<td valign="top">

5734



</td>
<td valign="top">

ERR\_MASKING\_UNKNOWN



</td>
<td valign="top">

Masking: unknown error occurred



</td>
</tr>
<tr>
<td valign="top">

5735



</td>
<td valign="top">

ERR\_MASKING\_INVALID\_MASK\_EXPRESSION



</td>
<td valign="top">

Masking: invalid mask expression



</td>
</tr>
<tr>
<td valign="top">

5736



</td>
<td valign="top">

ERR\_MASKING\_INVALID\_COLUMN\_DATATYPE



</td>
<td valign="top">

Masking: not supported data type



</td>
</tr>
<tr>
<td valign="top">

5737



</td>
<td valign="top">

ERR\_MASKING\_INVALID\_MASK\_COLUMN



</td>
<td valign="top">

Masking: invalid mask column



</td>
</tr>
</table>

**Related Information**  


[M\_ERROR\_CODES System View](../020-System-Views-Reference/022-Monitoring-Views/m-error-codes-system-view-20af1b5.md "Provides error codes with descriptions.")

