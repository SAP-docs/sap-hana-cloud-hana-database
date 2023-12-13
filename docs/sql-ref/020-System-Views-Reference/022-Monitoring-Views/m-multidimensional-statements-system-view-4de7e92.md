<!-- loio4de7e92c6015491aa380bdfe26070aa0 -->

# M\_MULTIDIMENSIONAL\_STATEMENTS System View

Displays the relationship between subqueries and the main query for asynchronous batch multidimensional services \(MDS\) requests.



## Structure


<table>
<tr>
<th valign="top">

COLUMN\_NAME

</th>
<th valign="top">

DATA\_TYPE\_NAME

</th>
<th valign="top">

COMMENTS

</th>
</tr>
<tr>
<td valign="top">

EXECUTION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the execution.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the MDS statement hash of the query or subquery.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the hash of parent MDS Statement \(the batch query\). This value is empty if it is not a sub query of a batch query.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the SQL Statement ID.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time.

</td>
</tr>
</table>

**Related Information**  


[SAP HANA Cloud, SAP HANA Database Configuration Parameter Reference](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-configuration-parameter-reference/sap-hana-configuration-parameter-reference-detail)

