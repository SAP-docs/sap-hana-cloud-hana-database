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

0

</td>
<td valign="top">

ERR\_LTT\_NO\_ERROR

</td>
<td valign="top">

Default constructed empty exception object

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

WRN\_GENERAL

</td>
<td valign="top">

general warning

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

general error

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

fatal error

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

cannot allocate enough memory

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

initialization error

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

invalid data

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

feature not supported

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

invalid argument

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

index out of bounds

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

authentication failed

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

invalid state

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

cannot open file

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

cannot create/write file

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

cannot allocate enough disk space

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

cannot find file

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

statement retry

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

metadata schema version incompatible between database and executable file

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

service shutting down

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

invalid license

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

connect attempt outside user's validity period

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

persistence error

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

transaction error

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

transaction rolled back by an internal error

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

transaction rolled back by integrity constraint violation

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

transaction rolled back by lock wait timeout

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

transaction rolled back due to unavailable resource

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

transaction rolled back by detected deadlock

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

failure in accessing checkpoint file

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

failure in accessing anchor file

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

failure in accessing log file

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

failure in accessing archive file

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

transaction serialization failure

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

current operation cancelled by request and transaction rolled back

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

invalid write-transaction identifier

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

failure in accessing invisible log file

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

exceed max num of concurrent transactions

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

transaction serialization failure until timeout expires

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

transaction rollback

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

transaction distribution work failure

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

Resource busy and NOWAIT specified

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

inconsistency between data and log

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

transaction start is blocked until Coordinator\_Restart finishes

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

distributed transaction commit failure

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

statement cancelled or snapshot timestamp already invalidated

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

transaction rollback

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

transaction rollback

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

transaction serialization failure

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

failure in acquiring index handle

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

transaction rollback

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

XA transaction error

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

asynchronous operation error

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

duplicate XID

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

invalid argument of XA call

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

no valid XID

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

outside of global transaction

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

improper XA call sequence

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

resource manager error

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

Resource manager unavailable

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

A protocol error occurred in the resource manager

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

The rollback was caused by an unspecified reason

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

sql processing error

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

sql syntax error

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

insufficient privilege

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

invalid table name

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

invalid column name

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

invalid index name

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

invalid query name

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

invalid alias name

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

invalid datatype

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

expression missing

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

inconsistent datatype

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

specified length too long for its datatype

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

column ambiguously defined

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

too many values

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

not enough values

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

duplicate alias

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

duplicate column name

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

not a single character string

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

inserted value too large for column

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

aggregate function not allowed

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

missing aggregation or grouping

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

not a GROUP BY expression

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

nested group function without GROUP BY

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

group function is nested

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

ORDER BY item must be the number of a SELECT-list

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

outer join not allowed in operand of OR or IN

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

two tables cannot be outer-joined to each other

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

a table may be outer joined to at most one other table

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

join field does not match

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

invalid join condition

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

identifier is too long

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

cannot insert NULL or update to NULL

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

cannot use duplicate table name

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

cannot use duplicate index name

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

cannot use duplicate query name

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

argument identifier must be positive

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

wrong number of arguments

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

argument type mismatch

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

cannot have more than one primary key

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

too long multi key length

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

replicated table must have a primary key

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

cannot update primary key field in replicated table

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

cannot store DDL

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

cannot drop index used for enforcement of unique/primary key

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

argument index is out of range

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

unique constraint violated

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

invalid CHAR or VARCHAR value

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

invalid DATE

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

division by zero undefined

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

single-row query returns more than one row

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

invalid cursor

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

numeric value out of range

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

column name already exists

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

correlated subquery cannot have TOP or ORDER BY

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

sql error in procedure

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

cannot drop all columns in a table

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

sequence is exhausted

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

invalid sequence

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

numeric overflow

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

invalid synonym

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

wrong number of arguments in function invocation

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

P\_QUERYPLANS not exists nor valid format

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

decimal precision specifier is out of range

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

decimal scale specifier is out of range

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

cannot create index on expression with datatype LOB

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

invalid view name

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

cannot use duplicate view name

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

duplicate replication id

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

cannot use duplicate sequence name

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

invalid escape sequence

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

CURRVAL of given sequence is not yet defined in this session

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

cannot explain plan of given statement

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

invalid name of function or procedure

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

cannot use duplicate name of function or procedure

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

cannot use duplicate synonym name

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

user name already exists

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

invalid user name

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

column not allowed

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

invalid user privilege

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

field alias name already exists

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

invalid default value

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

INTO clause not allowed for this SELECT statement

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

zero-length columns are not allowed

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

invalid number

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

not all variables bound

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

numeric underflow

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

collation conflict

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

invalid collate name

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

parse error in data loader

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

not a replication table

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

invalid replication id

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

invalid option

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

invalid datetime format

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

cannot CREATE UNIQUE INDEX; duplicate key found

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

cannot drop columns in the primary-key column list

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

column is referenced in a multi-column constraint

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

cannot create unique index on cdx table

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

update log group name already exists

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

invalid update log group name

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

the base table of the update log table must have a primary key

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

exceed maximum number of update log group

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

the base table already has a update log table

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

update log table can not have a update log table

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

string is too long

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

view WITH CHECK OPTION where-clause violation

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

data manipulation operation not legal on this view

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

invalid schema name

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

number of index columns exceeds its maximum

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

invalid partial key size

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

no matching primary key for this column list

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

referenced table does not have a primary key

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

number of referencing columns must match referenced columns

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

unique constraint not allowed on temporary table

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

exceed maximum view depth limit

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

cannot perform DIRECT INSERT operation on table with unique indexes

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

invalid XML document

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

invalid XPATH

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

invalid XML duration value

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

invalid XML function usage

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

invalid XML index operation

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

Python buildin procedure error

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

JIT operation error

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

invalid column view

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

table schema mismatch

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

fail to change run level

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

fail to restart

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

fail to collect all version garbage

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

invalid identifier

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

string is too long

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

could not restore session

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

cannot use duplicate schema name

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

table ambiguously defined

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

role already exists

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

invalid role name

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

invalid user type

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

invalidated view

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

can't assign cyclic role

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

roles must not receive a privilege with grant option

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

error revoking role

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

invalid user-defined type name

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

cannot use duplicate user-defined type name

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

invalid object name

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

cannot have more than one order by

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

role tree too deep

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

primary key not allowed on insert-only table

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

unique constraint not allowed on insert-only table

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

the user was already dropped before query execution

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

internal error

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

invalid \(non-existent\) structured privilege name

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

cannot use duplicate structured privilege name

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

INSERT

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

invalid date format

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

password or parameter required for user

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

multiple values for a parameter not supported

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

invalid privilege namespace

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

invalid table type

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

invalid password layout

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

last n passwords can not be reused

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

user is forced to change password

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

user is deactivated

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

user is locked; try again later

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

can't drop without CASCADE specification

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

invalid view query for creation

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

can't drop with RESTRICT specification

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

password change currently not allowed

</td>
</tr>
<tr>
<td valign="top">

421

</td>
<td valign="top">

ERR\_SQL\_FULLTEXT\_INDEX

</td>
<td valign="top">

cannot create fulltext index

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

privileges must be either all SQL or all from one namespace

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

AFL error

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

invalid name of package

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

duplicate package name

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

number of columns mismatch

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

can not reserve index id any more

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

invalid query plan id

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

integrity check failed

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

invalidated procedure

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

user's password will expire within few days

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

this syntax has been deprecated and will be removed in next release

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

null value found

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

invalid object ID

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

invalid expression

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

could not set system license

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

only commands for license handling are allowed in current state

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

invalid user parameter value

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

composite error

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

table type conversion error

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

this feature has been deprecated and will be removed in next release

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

number of columns exceeds its maximum

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

invalid calculation scenario name

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

package manager error

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

invalid trigger name

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

cannot use duplicate trigger name

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

backup could not be completed

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

recovery could not be completed

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

recovery strategy could not be determined

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

failed to unset system license

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

modification of subject table in trigger not allowed

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

invalid backup id

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

user does not have a password

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

wrong hint syntax

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

the predefined session variable cannot be set via SET command

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

not allowed for this role

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

duplicate constraint name

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

unsupported function included

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

invalidated function

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

invalid privilege for object

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

foreign key constraint violation

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

failed on update or delete by foreign key constraint violation

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

number of tables exceeds its maximum

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

SQL internal parse tree depth exceeds its maximum

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

Cannot execute trigger

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

no credential found

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

cannot use parameter variable

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

hint error

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

unsupported datatype on source

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

invalid data source configuration

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

invalid data source name

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

cannot use duplicate data source name

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

invalid adapter configuration

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

invalid adapter name

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

cannot use duplicate adapter name

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

invalid remote object name

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

credential exists

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

user defined function runtime error

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

invalid spatial attribute

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

invalid spatial unit of measure name

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

cannot use duplicate spatial unit of measure name

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

invalid spatial reference system name

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

cannot use duplicate spatial reference system name

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

invalid session group command

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

invalid definition of structured privilege

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

some of rows have failed to be imported

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

some of rows have failed to be imported

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

invalid database name

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

invalid EPM Model name

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

cannot use duplicate EPM Model name

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

invalid EPM Model definition

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

invalid EPM Query Source name

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

cannot use duplicate EPM Query Source name

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

invalid EPM Query Source definition

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

Table already Extended with right delta option

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

Table already Non-Extended

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

Extended Storage not found for table:

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

Memory for a record exceeds the limit

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

invalid stacked column search

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

predicates are required in a where clause

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

Invalid series data specification:

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

invalid name of task

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

cannot use duplicate name of task

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

invalid adapter location

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

cannot remove last location of adapter

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

invalid create

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

invalid agent name

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

cannot use duplicate agent name

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

invalid agent properties

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

cannot alter global temporary table in use or create/alter/drop index on the table

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

replication error

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

cannot execute DDL statement on replication table while replicating

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

failure in accessing anchor file

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

failure in accessing log file

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

replication table has not conflict report table

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

conflict report table already enabled

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

conflict report table already disabled

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

partition error

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

invalid partition spec

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

invalid partition id

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

invalid use of partition property

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

invalid partition range

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

invalid partition type

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

invalid partition column

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

invalid partition level

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

api error

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

cursor type of forward is not allowed

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

invalid statement

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

exceed maximum batch size

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

Server rejected the connection\(protocol version mismatch\)

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

this function can be called only in the case of single statement

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

this query does not have result set

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

connection does not exist

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

No more LOB data

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

operation is not permitted

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

invalid parameter is received from server

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

result set is currently invalid

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

next\(\) is not called for this result set

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

too many parameters are set

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

some parameters are missing

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

internal error

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

not supported type conversion

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

remote-only function

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

no more result row in result set

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

Specified parameter is not output parameter

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

LOB streaming is not permitted in auto-commit mode

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

session context error

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

failed to execute the external statement

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

session layer is not initialized yet

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

failed routed execution

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

too many session variables are set

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

cannot set read-only session variable

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

invalid LOB

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

remote temp table access failure

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

invalid xa join request

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

exceed maximum LOB size

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

failed to cleanup resources

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

exceed maximum number of prepared statements

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

invalid CESU-8 string

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

transaction rollback failure

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

maximum length of value for session variable exceeded

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

maximum length of key for session variable exceeded

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

execution aborted by timeout

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

encrypted data access is not permitted

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

remote connection does not exist

</td>
</tr>
<tr>
<td valign="top">

616

</td>
<td valign="top">

ERR\_API\_REJECTED\_BY\_WORKLOAD\_CLASS

</td>
<td valign="top">

rejected by workload class configuration

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

sql processing error

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

invalid remote subscription name

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

cannot use duplicate remote subscription name

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

invalid remote subscription definition

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

remote source refers to the adapter location

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

remote source has active remote subscriptions:

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

invalidated task

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

not supported syntax in trigger

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

nesting depth of trigger and procedure is exceeded

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

Pinned plan error

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

Remove pinned plan error

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

cannot use duplicate object name

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

schema ambiguously defined

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

row order already set on table

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

no row order on table set

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

licensing error

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

property value too long

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

request to cancel task was sent but task did not cancel before timeout was reached

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

cannot mutate the table during trigger or foreign key execution

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

cannot use duplicate workload class name

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

invalid workload class name

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

cannot use duplicate workload mapping name

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

invalid workload mapping name

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

user not allowed to connect from client

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

invalid agent group name

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

cannot use duplicate agent group name

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

agents are still set to this agent group.

</td>
</tr>
<tr>
<td valign="top">

667

</td>
<td valign="top">

ERR\_SQL\_TEXT\_MINING\_FAILURE

</td>
<td valign="top">

text mining error

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

ST\_Point columns support 2-dimensional points only

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

spatial error

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

part does not exist

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

cannot use duplicate library name

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

duplicate association name

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

invalid graph workspace name

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

cross database object found and skipped in exporting

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

cannot use duplicate graph workspace name

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

cannot use duplicate combination of workload mapping

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

check constraint violation

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

deprecated plan stabilizer error

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

deprecated plan stabilizer error - manager not found: please check if Plan Stabilizer is enabled

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

statement hint error

</td>
</tr>
<tr>
<td valign="top">

681

</td>
<td valign="top">

ERR\_SQL\_STATEMENT\_HINT\_COMMAND

</td>
<td valign="top">

statement hint error - error while processing statement hint command

</td>
</tr>
<tr>
<td valign="top">

682

</td>
<td valign="top">

ERR\_SQL\_STATEMENT\_HINT\_TABLE\_EMPTY

</td>
<td valign="top">

statement hint error - statement hint table is empty

</td>
</tr>
<tr>
<td valign="top">

683

</td>
<td valign="top">

ERR\_SQL\_STATEMENT\_HINT\_MAP\_LOAD\_ERROR

</td>
<td valign="top">

statement hint error - statement hint table is corrupt

</td>
</tr>
<tr>
<td valign="top">

684

</td>
<td valign="top">

ERR\_SQL\_STATEMENT\_HINT\_RECORD\_ALREADY\_EXISTS

</td>
<td valign="top">

statement hint error - statement hint record already exists

</td>
</tr>
<tr>
<td valign="top">

685

</td>
<td valign="top">

ERR\_SQL\_STATEMENT\_HINT\_RECORD\_DOES\_NOT\_EXIST

</td>
<td valign="top">

statement hint error - statement hint record does not exist

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

start task error

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

exceed lag time of RESULT\_LAG

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

I/O error occured on file write

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

duplicate rowid matched during merge into

</td>
</tr>
<tr>
<td valign="top">

690

</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_DEPRECATED

</td>
<td valign="top">

deprecated plan stability error

</td>
</tr>
<tr>
<td valign="top">

691

</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_COMMAND\_DEPRECATED

</td>
<td valign="top">

deprecated plan stability error - error while processing command

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

deprecated plan stability error - stored plan table is empty

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

deprecated plan stability error - stored plan table is corrupt

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

deprecated plan stability error - stored plan record already exists

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

deprecated plan stability error - stored plan record does not exist

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

deprecated plan stability error - cannot convert to abstract plan

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

Preactive key already exists

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

No preactive key exists

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

cannot use duplicate dependency rule name

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

no\_stacked\_column\_search\(throw\_error\) error

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

usergroup name already exists

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

invalid usergroup name

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

incorrect root keys backup password

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

usergroup cannot be dropped

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

Two concurrent statements performed the same grant operation

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

currently only AES-256-CBC is supported: invalid cipher

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

cannot use duplicate column key name

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

column keycopy already exists

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

keypair already exists

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

currently only RSA-OAEP-2048 is supported: invalid cipher

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

cannot use duplicate column key id

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

deprecated plan stabilizer stored plan error - migration error

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

keypair not owned by the creator of the column key

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

cannot drop the last key admin keycopy

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

cannot use a workload mapping with no properties

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

statement is stale

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

invalid key id

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

cannot update non-existent row

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

currency/unit conversion error

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

DDL is currently disabled in this session

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

rowid column is not found

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

cannot drop the last keycopy

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

keypair not owned by key admin

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

invalid name of library

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

invalidated library

</td>
</tr>
<tr>
<td valign="top">

726

</td>
<td valign="top">

ERR\_SQL\_INVALID\_BASE64\_STRING

</td>
<td valign="top">

invalid Base64 string

</td>
</tr>
<tr>
<td valign="top">

727

</td>
<td valign="top">

ERR\_SQL\_INV\_CACHE

</td>
<td valign="top">

invalid result cache name

</td>
</tr>
<tr>
<td valign="top">

728

</td>
<td valign="top">

ERR\_SQL\_EXST\_CACHE

</td>
<td valign="top">

cannot use duplicate result cache name

</td>
</tr>
<tr>
<td valign="top">

729

</td>
<td valign="top">

ERR\_SQL\_UNKNOWN\_SESSION

</td>
<td valign="top">

unknown session id

</td>
</tr>
<tr>
<td valign="top">

730

</td>
<td valign="top">

ERR\_SQL\_RECOMPILE\_WITHOUT\_FALLBACK

</td>
<td valign="top">

query recompilation is required for reoptimized plan generation

</td>
</tr>
<tr>
<td valign="top">

731

</td>
<td valign="top">

ERR\_SQL\_RECOMPILE\_WITH\_FALLBACK

</td>
<td valign="top">

query recompilation is required for legacy plan generation

</td>
</tr>
<tr>
<td valign="top">

732

</td>
<td valign="top">

ERR\_SQL\_FAIL\_AUTO\_MATCH\_CACHE

</td>
<td valign="top">

cannot find matching view

</td>
</tr>
<tr>
<td valign="top">

733

</td>
<td valign="top">

ERR\_SQL\_DDL\_ONLY\_OBJECT

</td>
<td valign="top">

no DML on DDL-only object

</td>
</tr>
<tr>
<td valign="top">

734

</td>
<td valign="top">

ERR\_SQL\_EMPTY\_COLUMN\_KEY

</td>
<td valign="top">

cannot use empty column encryption key

</td>
</tr>
<tr>
<td valign="top">

735

</td>
<td valign="top">

ERR\_SQL\_RECOMPILE\_WITH\_DISK

</td>
<td valign="top">

query recompilation is required for disk plan generation

</td>
</tr>
<tr>
<td valign="top">

736

</td>
<td valign="top">

ERR\_SQL\_REMOVE\_SQL\_PLAN\_CACHE\_SELECTIVE

</td>
<td valign="top">

invalid WHERE condition.

</td>
</tr>
<tr>
<td valign="top">

737

</td>
<td valign="top">

ERR\_SQL\_FUZZY\_SEARCH\_INDEX

</td>
<td valign="top">

cannot create fuzzy search index

</td>
</tr>
<tr>
<td valign="top">

738

</td>
<td valign="top">

ERR\_SQL\_INV\_TENANT

</td>
<td valign="top">

invalid tenant name

</td>
</tr>
<tr>
<td valign="top">

739

</td>
<td valign="top">

ERR\_SQL\_EXST\_TENANT

</td>
<td valign="top">

cannot use duplicate tenant name

</td>
</tr>
<tr>
<td valign="top">

740

</td>
<td valign="top">

ERR\_SQL\_TENANT\_IN\_USE

</td>
<td valign="top">

tenant in use

</td>
</tr>
<tr>
<td valign="top">

741

</td>
<td valign="top">

ERR\_SQL\_TENANT\_OBJECT\_ALREADY\_ADDED

</td>
<td valign="top">

object already added to tenant

</td>
</tr>
<tr>
<td valign="top">

742

</td>
<td valign="top">

ERR\_SQL\_INV\_ROLEGROUP

</td>
<td valign="top">

invalid rolegroup name

</td>
</tr>
<tr>
<td valign="top">

743

</td>
<td valign="top">

ERR\_SQL\_EXST\_ROLEGROUP

</td>
<td valign="top">

rolegroup name already exists

</td>
</tr>
<tr>
<td valign="top">

744

</td>
<td valign="top">

ERR\_SQL\_EXST\_ROLE\_IN\_ROLEGROUP

</td>
<td valign="top">

there are roles in the rolegroup

</td>
</tr>
<tr>
<td valign="top">

745

</td>
<td valign="top">

ERR\_SQL\_ROLE\_NOT\_IN\_ANY\_ROLEGROUP

</td>
<td valign="top">

role is not member of any rolegroup

</td>
</tr>
<tr>
<td valign="top">

746

</td>
<td valign="top">

ERR\_SQL\_DATABASE\_EXTERNAL\_KEY\_REVOKED

</td>
<td valign="top">

external key for database has been revoked

</td>
</tr>
<tr>
<td valign="top">

747

</td>
<td valign="top">

ERR\_SQL\_TENANT\_EXTERNAL\_KEY\_REVOKED

</td>
<td valign="top">

external key for tenant has been revoked

</td>
</tr>
<tr>
<td valign="top">

748

</td>
<td valign="top">

ERR\_SQL\_INV\_RESULT\_CACHE\_TYPE

</td>
<td valign="top">

invalid result cache type

</td>
</tr>
<tr>
<td valign="top">

749

</td>
<td valign="top">

ERR\_SQL\_RETRY\_BY\_INTERNAL\_CANCEL

</td>
<td valign="top">

current sql operation cancelled internally by SQL Plan Advisor

</td>
</tr>
<tr>
<td valign="top">

750

</td>
<td valign="top">

ERR\_SQL\_INDEX\_NOT\_SUPPORTED

</td>
<td valign="top">

cannot create index

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

session error

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

communication error

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

cannot bind a communication port

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

communication initialization error

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

I/O control error

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

connection failure

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

send error

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

receive error

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

cannot create a thread

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

error while parsing protocol

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

exceed maximum number of external connections

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

not supported version

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

invalid session id

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

unknown hostname

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

rejected as server is temporarily overloaded

</td>
</tr>
<tr>
<td valign="top">

1039

</td>
<td valign="top">

ERR\_SES\_LOOKUP\_PORT\_CONNECT

</td>
<td valign="top">

not supported to redirect connection with no database name by using low version of client library

</td>
</tr>
<tr>
<td valign="top">

1040

</td>
<td valign="top">

ERR\_SES\_FORCE\_REROUTE

</td>
<td valign="top">

failed to execute statement in routing by workload class configuration

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

data statistics error

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

no matching data statistics objects found

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

invalid result from query to remote source

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

specified table not found or not supported

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

error building data statistics object

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

data statistics object already exists

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

invalid combination of settings specified

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

usergroup error

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

user is not member of any usergroup

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

current and new usergroup are the same

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

unknown parameter for usergroup

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

unknown parameter set for usergroup

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

same parametername specified more than once

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

invalid value for usergroup parameter

</td>
</tr>
<tr>
<td valign="top">

1127

</td>
<td valign="top">

ERR\_USERGROUP\_DISABLE\_CONNECT\_BY\_GROUP\_MEMBER\_NOT\_ALLOWED

</td>
<td valign="top">

user is member of this usergroup

</td>
</tr>
<tr>
<td valign="top">

1128

</td>
<td valign="top">

ERR\_USERGROUP\_IMPLICIT\_DEDUCTION\_NOT\_POSSIBLE

</td>
<td valign="top">

usergroup cannot be deduced automatically when creator has more than one OPERATOR privilege; amend the SQL command with SET USERGROUP

</td>
</tr>
<tr>
<td valign="top">

1129

</td>
<td valign="top">

ERR\_USERGROUP\_INVALID\_CONNECT\_RESTRICTION

</td>
<td valign="top">

unknown connect restriction for usergroup

</td>
</tr>
<tr>
<td valign="top">

1130

</td>
<td valign="top">

ERR\_USERGROUP\_CONNECT\_RESTRICTION\_EXISTS

</td>
<td valign="top">

connect restriction already exists for usergroup

</td>
</tr>
<tr>
<td valign="top">

1131

</td>
<td valign="top">

ERR\_USERGROUP\_CONNECT\_RESTRICTION\_CHANGE\_LOCKS\_SESSION\_USER

</td>
<td valign="top">

connect restriction change locks out session user

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

plan stability error

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

plan stability error - cannot execute command

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

plan stability error - abstract sql plan table is empty

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

plan stability error - cannot load abstract sql plan

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

plan stability error - abstract sql plan record already exists

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

plan stability error - abstract sql plan record does not exist

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

cannot capture abstract sql plan

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

plan stability error - migration

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

cannot apply abstract sql plan

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

cannot deserialize abstract sql plan

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

plan stability error - update location first

</td>
</tr>
<tr>
<td valign="top">

1163

</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_RELATED\_OBJECT\_CHECK\_FAILED

</td>
<td valign="top">

plan stability error - related object mismatch

</td>
</tr>
<tr>
<td valign="top">

1164

</td>
<td valign="top">

ERR\_SQL\_PLAN\_STABILITY\_COMPRESSION\_ERROR

</td>
<td valign="top">

plan stability error - cannot compress abstract sql plan

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

sqlscript error

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

wrong number or types of parameters in call

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

output parameter not a variable

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

OUT and IN OUT parameters may not have default expressions

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

duplicate parameters are not permitted

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

at most one declaration is permitted in the declaration section

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

cursor must be declared by SELECT statement

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

identifier must be declared

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

expression cannot be used as an assignment target

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

Not allowed expression for INTO-target

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

expression is inappropriate as the left hand side of an assignment statement

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

expression is of wrong type

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

illegal loop control statement

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

not a condition variable

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

an INTO clause is expected in SELECT statement

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

not permitted statement

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

identifier is not a cursor

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

wrong number of values in the INTO list of a FETCH statement

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

unhandled user-defined exception

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

no data found

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

fetch returns more than requested number of rows

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

numeric or value error

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

parallelizable function cannot have OUT or IN OUT parameter

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

user-defined exception

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

cursor is already opened

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

return type is invalid

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

return type mismatch

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

unsupported datatype is used

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

illegal single assignment

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

invalid use of table variable

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

scalar type is not allowed

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

Out parameter is not specified

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

At most one output parameter is allowed

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

output parameter should be a table or a table variable

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

invalid or reserved variable name

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

Function name exceeds maximum length limitation

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

1338

</td>
<td valign="top">

ERR\_SQLSCRIPT\_CE\_CONVERSION\_CUSTOM\_TAB\_MISSING

</td>
<td valign="top">

Cannot find table used in CE\_CONVERSION

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

1342

</td>
<td valign="top">

ERR\_SQLSCRIPT\_CE\_CALC\_ATTRIBUTE\_AND\_ALIAS\_ARE\_SAME

</td>
<td valign="top">

Attribute has the same name as the alias

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

not allowed concurrent write

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

not allowed concurrent read and write

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

datatype mismatch in CE function

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

Require USING statement before use

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

Surpassed expected library member count

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

Invalid input

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

Invalid pragma

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

The depth of the sqlscript callstack is too deep

</td>
</tr>
<tr>
<td valign="top">

1363

</td>
<td valign="top">

ERR\_SQLSCRIPT\_USER\_CONDITION

</td>
<td valign="top">

User-defined condition

</td>
</tr>
<tr>
<td valign="top">

1364

</td>
<td valign="top">

ERR\_SQLSCRIPT\_ASYNC\_CALL\_INIT\_FAILED

</td>
<td valign="top">

Asynchronous procedure call initialization failed

</td>
</tr>
<tr>
<td valign="top">

1365

</td>
<td valign="top">

ERR\_SQLSCRIPT\_ASYNC\_CALL\_CANCELLATION\_FAILED

</td>
<td valign="top">

Asynchronous procedure call cancellation failed

</td>
</tr>
<tr>
<td valign="top">

1536

</td>
<td valign="top">

ERR\_STATISTISTICS\_MONITOR\_INTERNAL\_ERROR

</td>
<td valign="top">

System monitor internal error

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

Configuration error:

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

Configuration warning:

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

no segment exists for the given key

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

invalid shmid

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

allow read access for shmid

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

shmid points to a removed identifier

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

invalid shmid

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

1840

</td>
<td valign="top">

ERR\_TZ

</td>
<td valign="top">

timezone error

</td>
</tr>
<tr>
<td valign="top">

1841

</td>
<td valign="top">

ERR\_TZ\_INVALID\_DATASET

</td>
<td valign="top">

invalid timezone dataset specified

</td>
</tr>
<tr>
<td valign="top">

1842

</td>
<td valign="top">

ERR\_TZ\_DATA\_NOT\_AVAILABLE

</td>
<td valign="top">

timezone data not available \(please see SAP note 1791342\)

</td>
</tr>
<tr>
<td valign="top">

1843

</td>
<td valign="top">

ERR\_TZ\_NOT\_FOUND

</td>
<td valign="top">

timezone not found

</td>
</tr>
<tr>
<td valign="top">

1844

</td>
<td valign="top">

ERR\_TZ\_FAILED

</td>
<td valign="top">

timezone calculation failed

</td>
</tr>
<tr>
<td valign="top">

1856

</td>
<td valign="top">

ERR\_SQL\_PLAN\_EXECUTION\_MONITOR\_GENERAL

</td>
<td valign="top">

\[SQL Plan Execution Monitor\] general error

</td>
</tr>
<tr>
<td valign="top">

1888

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_NOT\_AVAILABLE

</td>
<td valign="top">

HANA Database service is not available

</td>
</tr>
<tr>
<td valign="top">

1889

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_NOT\_AVAILABLE\_CCEK

</td>
<td valign="top">

HANA Database service not available because of revoked customer-controlled encryption key \(CCEK\)

</td>
</tr>
<tr>
<td valign="top">

1890

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_STOPPED

</td>
<td valign="top">

HANA Database service is stopped

</td>
</tr>
<tr>
<td valign="top">

1891

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_STARTING

</td>
<td valign="top">

HANA Database service is starting

</td>
</tr>
<tr>
<td valign="top">

1892

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_STOPPING

</td>
<td valign="top">

HANA Database service is stopping

</td>
</tr>
<tr>
<td valign="top">

1893

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_UPGRADE

</td>
<td valign="top">

HANA Database service upgrade in progress

</td>
</tr>
<tr>
<td valign="top">

1894

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_RESIZE

</td>
<td valign="top">

HANA Database service resize in progress

</td>
</tr>
<tr>
<td valign="top">

1895

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_RECOVERY

</td>
<td valign="top">

HANA Database service recovery in progress

</td>
</tr>
<tr>
<td valign="top">

1896

</td>
<td valign="top">

ERR\_URS\_INSTANCE\_MAINTENANCE

</td>
<td valign="top">

HANA Database service is in maintenance mode

</td>
</tr>
<tr>
<td valign="top">

1920

</td>
<td valign="top">

ERR\_VECTOR\_INVALID\_FORMAT

</td>
<td valign="top">

Invalid vector format

</td>
</tr>
<tr>
<td valign="top">

1921

</td>
<td valign="top">

ERR\_VECTOR\_DIMENSION\_MISMATCH

</td>
<td valign="top">

Vector dimension mismatch

</td>
</tr>
<tr>
<td valign="top">

1922

</td>
<td valign="top">

ERR\_VECTOR\_NUMERICAL\_ISSUE

</td>
<td valign="top">

Numerical issue in vector similarity function

</td>
</tr>
<tr>
<td valign="top">

1952

</td>
<td valign="top">

ERR\_REMOTE\_SUBSCRIPTION

</td>
<td valign="top">

Remote subscription error

</td>
</tr>
<tr>
<td valign="top">

1953

</td>
<td valign="top">

ERR\_REMOTE\_SUBSCRIPTION\_IN\_INITIAL\_LOAD\_PHASE

</td>
<td valign="top">

Remote subscription in initial load phasea

</td>
</tr>
<tr>
<td valign="top">

1954

</td>
<td valign="top">

ERR\_REMOTE\_SUBSCRIPTION\_IN\_DELTA\_LOAD\_PHASE

</td>
<td valign="top">

Remote subscription in delta load phase

</td>
</tr>
<tr>
<td valign="top">

1955

</td>
<td valign="top">

ERR\_REMOTE\_SUBSCRIPTION\_INITIAL\_LOAD\_CHUNK\_ALREADY\_LOADED

</td>
<td valign="top">

Initial load chunk already loaded

</td>
</tr>
<tr>
<td valign="top">

1956

</td>
<td valign="top">

ERR\_REMOTE\_SUBSCRIPTION\_DELTA\_LOAD\_VERSION\_ALREADY\_LOADED

</td>
<td valign="top">

Delta load version already loaded

</td>
</tr>
<tr>
<td valign="top">

1957

</td>
<td valign="top">

ERR\_REMOTE\_SUBSCRIPTION\_COLUMN\_MISMATCH

</td>
<td valign="top">

Schema mismatch between source and target tables

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

delta log replay failed

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

metadata update not supported in worker node

</td>
</tr>
<tr>
<td valign="top">

2569

</td>
<td valign="top">

ERR\_DIST\_METADATA\_COORDINATOR\_UPDATE\_FAILURE

</td>
<td valign="top">

metadata update in coordinator indexserver is failed

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

attempt to access metadata of an invalid address \(already deleted or corrupted

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

can not find catalog object

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

can not make cyclic dependency

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

SqlScript Builtin Function

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

2875

</td>
<td valign="top">

ERR\_SQLSCRIPT\_RLANG\_EXACTLY\_ONE\_OUTPUT\_PARAM

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

Invalid action for tenant specific audit policy

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

Number of days for retention too small or no retention for used trail types allowed at all

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

general LDAP error

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

Local authorization not allowed

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

Authorization mode change not allowed

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

Role to LDAP group mapping already exists

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

Role to LDAP group mapping does not exist

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

Creating LDAP provider failed because of internal error

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

Deleting LDAP provider failed because of internal error

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

Alter LDAP provider failed because of internal error

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

Validate LDAP provider failed because of internal error

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

LDAP provider already exists

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

Invalid LDAP provider name

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

Credentials not provided in proper format

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

Local password authentication and LDAP authentication cannot be enabled together for the same user

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

Creating provider failed because of internal error

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

Deleting provider failed because of internal error

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

Alter provider failed because of internal error

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

Duplicate provider for this issuer

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

Duplicate identity for this provider

</td>
</tr>
<tr>
<td valign="top">

4241

</td>
<td valign="top">

ERR\_PROVIDER\_HAS\_USER\_MAPPINGS

</td>
<td valign="top">

Provider has user mappings

</td>
</tr>
<tr>
<td valign="top">

4242

</td>
<td valign="top">

ERR\_PROVIDER\_DROPPING\_USER\_MAPPING\_FAILED

</td>
<td valign="top">

Dropping a provider user mapping failed

</td>
</tr>
<tr>
<td valign="top">

4243

</td>
<td valign="top">

ERR\_PROVIDER\_DUPLICATE\_SUBJECT\_ISSUER

</td>
<td valign="top">

Duplicate provider for this subject and this issuer

</td>
</tr>
<tr>
<td valign="top">

4244

</td>
<td valign="top">

ERR\_PROVIDER\_INVALID\_ATTRIBUTE

</td>
<td valign="top">

Invalid attribute

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

4294

</td>
<td valign="top">

ERR\_X509\_INV\_MATCHING\_RULE

</td>
<td valign="top">

Invalid matching rule layout

</td>
</tr>
<tr>
<td valign="top">

4295

</td>
<td valign="top">

ERR\_X509\_DISABLED

</td>
<td valign="top">

X.509 feature disabled

</td>
</tr>
<tr>
<td valign="top">

4296

</td>
<td valign="top">

ERR\_X509\_NO\_MATCHING\_RULES

</td>
<td valign="top">

Provider has no matching rules

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

Invalid data flow package name

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

General dpserver error occured

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

Adapter failure

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

Source table dropped in the remote source

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

Invalid scheduler job name

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

Cannot use duplicate scheduler job name

</td>
</tr>
<tr>
<td valign="top">

4738

</td>
<td valign="top">

ERR\_INV\_USABLE\_SCHEDULER\_JOB

</td>
<td valign="top">

Invalidated scheduler job

</td>
</tr>
<tr>
<td valign="top">

4900

</td>
<td valign="top">

ERR\_GRAPH\_UNKNOWN

</td>
<td valign="top">

GraphEngine: unknown error occurred

</td>
</tr>
<tr>
<td valign="top">

4901

</td>
<td valign="top">

ERR\_GRAPH\_COMPILATION\_FAILED

</td>
<td valign="top">

GraphEngine: compilation failed

</td>
</tr>
<tr>
<td valign="top">

4902

</td>
<td valign="top">

ERR\_GRAPH\_COMPILATION\_WARNING

</td>
<td valign="top">

GraphEngine: compilation warning occurred

</td>
</tr>
<tr>
<td valign="top">

4903

</td>
<td valign="top">

ERR\_GRAPH\_INTERNAL

</td>
<td valign="top">

GraphEngine: internal error

</td>
</tr>
<tr>
<td valign="top">

4904

</td>
<td valign="top">

ERR\_GRAPH\_NOT\_SUPPORTED

</td>
<td valign="top">

GraphEngine: feature not supported

</td>
</tr>
<tr>
<td valign="top">

4905

</td>
<td valign="top">

ERR\_GRAPH\_OPENCYPHER\_SYNTAX\_ERROR

</td>
<td valign="top">

GraphEngine: OpenCypher syntax error

</td>
</tr>
<tr>
<td valign="top">

4906

</td>
<td valign="top">

ERR\_GRAPH\_OPENCYPHER\_COMPILATION\_ERROR

</td>
<td valign="top">

GraphEngine: OpenCypher compilation error

</td>
</tr>
<tr>
<td valign="top">

4907

</td>
<td valign="top">

ERR\_GRAPH\_GRAPHSCRIPT\_RUNTIME\_ERROR

</td>
<td valign="top">

GraphEngine: runtime error during graphscript execution

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

Certificate already exists

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

5649

</td>
<td valign="top">

ERR\_CERTADM\_OBJECT\_NOT\_FOUND

</td>
<td valign="top">

Purpose object not found

</td>
</tr>
<tr>
<td valign="top">

5650

</td>
<td valign="top">

ERR\_CERTADM\_OBJECT\_ALREADY\_IN\_USE

</td>
<td valign="top">

Purpose object already in use by another PSE

</td>
</tr>
<tr>
<td valign="top">

5651

</td>
<td valign="top">

ERR\_CERTADM\_INVALID\_HOSTNAME

</td>
<td valign="top">

Invalid hostname format

</td>
</tr>
<tr>
<td valign="top">

5652

</td>
<td valign="top">

ERR\_CERTADM\_PSE\_WITHOUT\_OTHER\_PURPOSE\_OBJECT

</td>
<td valign="top">

PSE has no other purpose object

</td>
</tr>
<tr>
<td valign="top">

5653

</td>
<td valign="top">

ERR\_CERTADM\_PSE\_WITHOUT\_OTHER\_HOST

</td>
<td valign="top">

PSE has no other host

</td>
</tr>
<tr>
<td valign="top">

5654

</td>
<td valign="top">

ERR\_CERTADM\_CERTIFICATE\_EXPIRED

</td>
<td valign="top">

Certificate is already expired

</td>
</tr>
<tr>
<td valign="top">

5655

</td>
<td valign="top">

ERR\_CERTADM\_CHAIN\_CERTIFICATE\_EXPIRED

</td>
<td valign="top">

Invalid certificate chain: contains expired certificates

</td>
</tr>
<tr>
<td valign="top">

5656

</td>
<td valign="top">

ERR\_CERTADM\_UNSET\_OWN\_WITH\_PURPOSE

</td>
<td valign="top">

Can't unset own certificate if the PSE still has the purpose SSL

</td>
</tr>
<tr>
<td valign="top">

5657

</td>
<td valign="top">

ERR\_CERTADM\_PSE\_PURPOSE\_BLOCKED\_BY\_CONFIG

</td>
<td valign="top">

PSE purpose blocked by configuration

</td>
</tr>
<tr>
<td valign="top">

5658

</td>
<td valign="top">

ERR\_CERTADM\_INVALID\_PUBKEY\_DEFINITION

</td>
<td valign="top">

Public key definition invalid or not supported

</td>
</tr>
<tr>
<td valign="top">

5659

</td>
<td valign="top">

ERR\_CERTADM\_EXST\_PUBKEY

</td>
<td valign="top">

Public key with same name already exists

</td>
</tr>
<tr>
<td valign="top">

5660

</td>
<td valign="top">

ERR\_CERTADM\_NON\_EXST\_PUBKEY

</td>
<td valign="top">

Public key could not be found

</td>
</tr>
<tr>
<td valign="top">

5661

</td>
<td valign="top">

ERR\_CERTADM\_PUBKEY\_IN\_USE

</td>
<td valign="top">

Public key could not be dropped because it is still in use by at least one PSE

</td>
</tr>
<tr>
<td valign="top">

5662

</td>
<td valign="top">

ERR\_CERTADM\_NO\_SUCH\_PUBKEY\_IN\_PSE

</td>
<td valign="top">

PSE does not contain such public key

</td>
</tr>
<tr>
<td valign="top">

5663

</td>
<td valign="top">

ERR\_CERTADM\_RELOAD\_PSE\_FAILURE

</td>
<td valign="top">

Error reloading file-based PSEs

</td>
</tr>
<tr>
<td valign="top">

5712

</td>
<td valign="top">

ERR\_PFCG\_INVALID\_CONFIGURATION

</td>
<td valign="top">

Pfcg: invalid configuration

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
<tr>
<td valign="top">

5920

</td>
<td valign="top">

ERR\_REMOTE\_UNKNOWN

</td>
<td valign="top">

Unable to use remote source

</td>
</tr>
<tr>
<td valign="top">

5921

</td>
<td valign="top">

ERR\_REMOTE\_CONNECTION

</td>
<td valign="top">

Unable to connect remote source

</td>
</tr>
<tr>
<td valign="top">

5922

</td>
<td valign="top">

ERR\_REMOTE\_FETCH

</td>
<td valign="top">

Unable to fetch from remote source

</td>
</tr>
<tr>
<td valign="top">

5923

</td>
<td valign="top">

ERR\_REMOTE\_CREATE

</td>
<td valign="top">

Unable to create remote source

</td>
</tr>
</table>

**Related Information**  


[M\_ERROR\_CODES System View](../020-System-Views-Reference/022-Monitoring-Views/m-error-codes-system-view-20af1b5.md "Provides error codes with descriptions.")

