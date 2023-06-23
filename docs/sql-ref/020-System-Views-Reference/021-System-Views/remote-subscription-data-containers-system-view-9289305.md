<!-- loio9289305ea87d4984bcdd2453b678e5e4 -->

# REMOTE\_SUBSCRIPTION\_DATA\_CONTAINERS System View

Provides information regarding remote subscription data.



<a name="loio9289305ea87d4984bcdd2453b678e5e4__section_y1z_dtw_h1b"/>

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

REMOTE\_SOURCE\_NAME



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the remote source name.



</td>
</tr>
<tr>
<td valign="top">

CONTENT\_TYPE



</td>
<td valign="top">

NVARCHAR\(40\)



</td>
<td valign="top">

Displays the category of data containers:

-   COMMIT SEQUENCE GROUP
-   COMMIT SEQUENCES \(displays the order that transactions get committed and a sequence number for each commit row\)
-   TRANSACTION \(each container contains only one transaction\)
-   LOBS
-   ROLLBACK SAVEPOINTS
-   DISTRIBUTOR QUEUE DATA \(displays the data currently being queued by the distributor\)
-   DISTRIBUTOR QUEUE DATA REFERENCES \(displays the list of transactions currently being referenced by the distributor\)



</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the remote subscription.



</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the remote subscription.



</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_ID



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the ID of the transaction being replicated.



</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the data container. Depending on the content type, a container can be searched by REMOTE\_SOURCE\_ID and CONTENT\_TYPE or with additional information such as SUBSCRIPTION\_OID or TRANSACTION\_ID.



</td>
</tr>
</table>

**Related Information**  


[REMOTE\_SUBSCRIPTIONS System View](remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[CREATE REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/12d89b67c7994f80bc516e30dadd3c0a.html)

[ALTER REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/f88b70b3170849b0a57d4ff618887dce.html)

[DROP REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/af65fc25d26c4968ac1448cf13056432.html)

