<!-- loio96491c85116a452bb2a85b46528515e7 -->

# M\_FEATURE\_USAGE System View

Provides detailed feature usage statistics.



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

COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the component name.

</td>
</tr>
<tr>
<td valign="top">

FEATURE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the feature name.

</td>
</tr>
<tr>
<td valign="top">

IS\_DEPRECATED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not a feature is deprecated: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the counter tracking the number of artifacts that belong to the feature, for example, the number of existing history tables.

</td>
</tr>
<tr>
<td valign="top">

CALL\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the counter tracking the number of times that the feature has been used since the last start of the indexserver, for example, the number of accesses to any history table.

</td>
</tr>
<tr>
<td valign="top">

LAST\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP\(27\)

</td>
<td valign="top">

Displays the last point in time when the feature was used. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID of the last feature usage. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database user of the last feature usage, for example, SAP *<SID\>*. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user of the last feature usage, for example, *<D-User\>*. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application name of the last feature usage. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application source name and location of the last feature usage. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the statement ID of the last feature usage. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the statement hash of the last feature usage. By default, the value is deprecated if this configuration has not changed.

</td>
</tr>
</table>



<a name="loio96491c85116a452bb2a85b46528515e7__section_a53_4xd_xsb"/>

## Native Storage Extension Feature Monitoring

Native Storage Extension \(NSE\) feature usage statistics can be seen in M\_FEATURE\_USAGE monitoring view.

Under the component name NSE, object count for table, column , partition and index are shown.

> ### Note:  
> OBJECT\_COUNT here indicates the number of objects \(table, column, partition, index\) which have load unit defined as page-loadable.



### Examples

**TABLE**


<table>
<tr>
<th valign="top">

COMPONENT\_NAME

</th>
<th valign="top">

FEATURE\_NAME

</th>
<th valign="top">

IS\_DEPRECATED

</th>
<th valign="top">

OBJECT\_COUNT

</th>
<th valign="top">

OTHER COLUMNS

</th>
</tr>
<tr>
<td valign="top">

NSE

</td>
<td valign="top">

TABLE

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

10

</td>
<td valign="top">

?

</td>
</tr>
</table>

**COLUMN**


<table>
<tr>
<th valign="top">

COMPONENT\_NAME

</th>
<th valign="top">

FEATURE\_NAME

</th>
<th valign="top">

IS\_DEPRECATED

</th>
<th valign="top">

OBJECT\_COUNT

</th>
<th valign="top">

OTHER COLUMNS

</th>
</tr>
<tr>
<td valign="top">

NSE

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

12

</td>
<td valign="top">

?

</td>
</tr>
</table>

**PARTITION**


<table>
<tr>
<th valign="top">

COMPONENT\_NAME

</th>
<th valign="top">

FEATURE\_NAME

</th>
<th valign="top">

IS\_DEPRECATED

</th>
<th valign="top">

OBJECT\_COUNT

</th>
<th valign="top">

OTHER COLUMNS

</th>
</tr>
<tr>
<td valign="top">

NSE

</td>
<td valign="top">

PARTITION

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

15

</td>
<td valign="top">

?

</td>
</tr>
</table>

**INDEX**


<table>
<tr>
<th valign="top">

COMPONENT\_NAME

</th>
<th valign="top">

FEATURE\_NAME

</th>
<th valign="top">

IS\_DEPRECATED

</th>
<th valign="top">

OBJECT\_COUNT

</th>
<th valign="top">

OTHER COLUMNS

</th>
</tr>
<tr>
<td valign="top">

NSE

</td>
<td valign="top">

INDEX

</td>
<td valign="top">

FALSE

</td>
<td valign="top">

2

</td>
<td valign="top">

?

</td>
</tr>
</table>

**Related Information**  


[M\_FEATURES System View](m-features-system-view-20afe0e.md "Provides information about all supported features.")

