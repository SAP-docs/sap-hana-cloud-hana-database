<!-- loiod73be7e8ed40499c9ae0a8baf711c5d8 -->

# M\_OBJECTS

Shows the database objects in the run-time schema of an HDI container.



The SAP HDI Container API includes the `M_OBJECTS` view, which shows the database objects that are present in the container’s run-time schema. This includes all objects that have been deployed as well as all objects that have been created manually. The view also shows information about the validity of the objects and the object's owners. This view is intended to help troubleshoot issues that may arise from objects becoming invalid, deleted, or created with the wrong user.



**M\_OBJECTS**


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

CONTAINER\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

The name of the HDI container hosting the objects

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The object’s remote source name, if applicable

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The object’s database name

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The object’s database schema name

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the container object

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">

The type of the container object

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

The object’s file path, if it is an object deployed by the container

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

The object's validity \(“TRUE” or “FALSE”\)

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_VERSION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The metadata version of the container object

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The object’s ID

</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the owner of the container object

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the object that the current object depends on, for example, a synonym if the current object is the synonym’s target object

</td>
</tr>
</table>



<a name="loiod73be7e8ed40499c9ae0a8baf711c5d8__section_yrt_qqc_kgb"/>

## Examples

Select all objects that were manually created in run-time schema of the container “C”:

```
SELECT * FROM C#DI.M_OBJECTS WHERE PATH IS NULL
```

Select all objects in container “C” which are no longer owned by the container’s object owner:

```
SELECT * FROM C#DI.M_OBJECTS WHERE PATH IS NOT NULL AND OWNER_NAME != 'C#OO' 
```

Select all objects that should be deployed in container “C”, but have been manually deleted:

```
SELECT * FROM C#DI.M_OBJECTS WHERE PATH IS NOT NULL AND OBJECT_TYPE IS NULL
```

Select all invalid objects in container “C”:

```
SELECT * FROM C#DI.M_OBJECTS WHERE IS_VALID='FALSE' 
```

**Related Information**  


[HDI Container Views](hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

