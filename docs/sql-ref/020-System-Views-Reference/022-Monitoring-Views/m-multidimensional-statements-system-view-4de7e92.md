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
<tr>
<td valign="top">

EXECUTION\_MEMORY\_SIZE<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the peak memory usage, in bytes, of the query.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_CPU\_TIME<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU time in used in ms.

</td>
</tr>
</table>



<a name="loio4de7e92c6015491aa380bdfe26070aa0__section_n2h_4fs_dyb"/>

## Additional Information

<sup>\*\*</sup>Only memory usage and CPU time on the main system is tracked. If any other system is involved, for example, an external view is used, then memory usage and CPU time on this system is not tracked. For batch queries, there is always one entry for the complete query and one for each sub query. To avoid a double counting of memory and CPU time, the following rules apply:


<dl>
<dt><b>

Normal Batch Request:

</b></dt>
<dd>

The memory usage is tracked for the complete query, while CPU-Time is tracked for each sub query.

-   Batch query:
    -   EXECUTION\_MEMORY\_SIZE is the memory-usage of all subqueries together.
    -   EXECUTION\_CPU\_TIME is NULL.

-   Sub queries:
    -   EXECUTION\_MEMORY\_SIZE is NULL.
    -   EXECUTION\_CPU\_TIME is the CPU time used by the subquery.




</dd><dt><b>

Asynchronous Batch Request:

</b></dt>
<dd>

For asynchronous batch requests, both CPU time and memory usage are tracked per subquery.

-   Batch query:
    -   Both EXECUTION\_MEMORY\_SIZE and EXECUTION\_CPU\_TIME are null.

-   Sub queries:
    -   EXECUTION\_MEMORY\_SIZE is the memory used by the subquery.
    -   EXECUTION\_CPU\_TIME is the CPU time used by the subquery.




</dd>
</dl>

The M\_MULTIDIMENSIONAL\_STATEMENTS view is not enabled by default. Refer to the *mds* section in the *SAP HANA Cloud, SAP HANA Database Configuration Parameter Reference* for details on enabling.

**Related Information**  


[SAP HANA Cloud, SAP HANA Database Configuration Parameter Reference](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-configuration-parameter-reference/sap-hana-configuration-parameter-reference-detail)

