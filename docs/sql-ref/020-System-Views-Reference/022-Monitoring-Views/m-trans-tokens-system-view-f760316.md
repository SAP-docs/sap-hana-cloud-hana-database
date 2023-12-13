<!-- loiof76031621d4c4947ac32dbf257844b3b -->

# M\_TRANS\_TOKENS System View

Provides information about all active transaction tokens.



## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

TRANS\_TOKEN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the transaction token ID.

</td>
</tr>
<tr>
<td valign="top">

PRIMARY\_TRANS\_TOKEN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the primary transaction token ID for the shipped transaction token. If the transaction token is local-only, then this has the same value as TRANS\_TOKEN\_ID.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the associated transaction object ID.

</td>
</tr>
<tr>
<td valign="top">

LOGICAL\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the associated logical connection ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the associated logical statement ID.

</td>
</tr>
<tr>
<td valign="top">

MVCC\_SNAPSHOT\_TIMESTAMP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the MVCC timestamp that is held by the transaction token.

</td>
</tr>
<tr>
<td valign="top">

MVCC\_SNAPSHOT\_SCOPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the MVCC snapshot scope: TABLE/GLOBAL.

</td>
</tr>
</table>

**Related Information**  


[M\_TRANSACTIONS System View](m-transactions-system-view-20c9610.md "Provides information about all transactions created by users or the database.")

[IS\_SQL\_INJECTION\_SAFE Function \(Security\)](../../010-SQL-Reference/011-SQL-Functions/is-sql-injection-safe-function-security-4496cc5.md "Checks a specified SQL identifier for possible SQL injection risks.")

