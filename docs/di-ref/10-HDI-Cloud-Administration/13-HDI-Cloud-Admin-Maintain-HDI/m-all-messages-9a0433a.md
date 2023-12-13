<!-- loio9a0433a309f44e5e857fcc313233c91f -->

# M\_ALL\_MESSAGES

Shows all messages for an HDI container group.



The `_SYS_DI` monitoring view `M_ALL_MESSAGES` shows all HDI-container-group messages of all HDI container groups.



**M\_ALL\_MESSAGES**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

REQUEST\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The unique ID of the API call that produced this message. This ID is always the same for messages that originate from the same API call.

</td>
</tr>
<tr>
<td valign="top">

ROW\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

An increasing number representing the line number of the message log

</td>
</tr>
<tr>
<td valign="top">

LEVEL

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The indentation level of the message \(used for better visual representation\)

</td>
</tr>
<tr>
<td valign="top">

TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

The type of message:

-   SUMMARY: summary of the API call

-   HDI: message from HDI itself

-   PLUGIN: message from an HDI plug-in




</td>
</tr>
<tr>
<td valign="top">

LIBRARY\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

\(**optional**\) The ID of the library \(for messages from a plug-in\)

</td>
</tr>
<tr>
<td valign="top">

PLUGIN\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

\(**optional**\) The ID of the plug-in \(for messages from a plug-in\)

</td>
</tr>
<tr>
<td valign="top">

PATH

</td>
<td valign="top">

NVARCHAR\(511\)

</td>
<td valign="top">

\(**optional**\) The path to the artifact that is being processed

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

The severity of the message \(INFO, WARNING, ERROR\)

</td>
</tr>
<tr>
<td valign="top">

MESSAGE\_CODE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

A unique code corresponding to the `MESSAGE` field

</td>
</tr>
<tr>
<td valign="top">

MESSAGE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

The text of the message

</td>
</tr>
<tr>
<td valign="top">

LOCATION

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

\(**optional**\) The position \(line:column\) within the artifact that the message refers to

</td>
</tr>
<tr>
<td valign="top">

LOCATION\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

\(**optional**\) XPath expression within the artifact that the message refers to

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP\_UTC

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The time when the message was created

</td>
</tr>
</table>

**Related Information**  


[M\_JOBS](../../20-HDI-Cloud-Content-Development/m-jobs-d114ced.md "View information about the progress of jobs belonging to a MAKE operation.")

[M\_ROLES](../../20-HDI-Cloud-Content-Development/m-roles-b7f3bee.md "Show the roles that are deployed in an HDI container.")

