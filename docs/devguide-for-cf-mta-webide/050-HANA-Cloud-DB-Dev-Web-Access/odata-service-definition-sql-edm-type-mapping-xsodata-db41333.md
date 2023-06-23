<!-- loiodb41333d80e7490087224e9d6a0ca9b5 -->

# OData Service Definition: SQL-EDM Type Mapping \(XSOData\)

During the activation of the OData service definition, the SAP HANA SQL types are mapped to the required OData EDM types according to the rules specified in a mapping table.



The following mapping table lists how SAP HANA SQL types are mapped to OData EDM types during the activation of an OData service definition.

> ### Note:  
> The OData implementation in SAP HANA XSOData supports only those SQL types listed in the following table.

**SAP HANA SQL to OData EDM Type Mapping**


<table>
<tr>
<th valign="top">

SAP HANA SQL Type



</th>
<th valign="top">

OData EDM Type



</th>
</tr>
<tr>
<td valign="top">

Time



</td>
<td valign="top">

Edm.Time



</td>
</tr>
<tr>
<td valign="top">

Date



</td>
<td valign="top">

Edm.DateTime



</td>
</tr>
<tr>
<td valign="top">

SecondDate



</td>
<td valign="top">

Edm.DateTime



</td>
</tr>
<tr>
<td valign="top">

LongDate



</td>
<td valign="top">

Edm.DateTime



</td>
</tr>
<tr>
<td valign="top">

Timestamp



</td>
<td valign="top">

Edm.DateTime



</td>
</tr>
<tr>
<td valign="top">

TinyInt



</td>
<td valign="top">

Edm.Byte



</td>
</tr>
<tr>
<td valign="top">

SmallInt



</td>
<td valign="top">

Edm.Int16



</td>
</tr>
<tr>
<td valign="top">

Integer



</td>
<td valign="top">

Edm.Int32



</td>
</tr>
<tr>
<td valign="top">

BigInt



</td>
<td valign="top">

Edm.Int64



</td>
</tr>
<tr>
<td valign="top">

SmallDecimal



</td>
<td valign="top">

Edm.Decimal



</td>
</tr>
<tr>
<td valign="top">

Decimal



</td>
<td valign="top">

Edm.Decimal



</td>
</tr>
<tr>
<td valign="top">

Real



</td>
<td valign="top">

Edm.Single



</td>
</tr>
<tr>
<td valign="top">

Float



</td>
<td valign="top">

Edm.Single



</td>
</tr>
<tr>
<td valign="top">

Double



</td>
<td valign="top">

Edm.Double



</td>
</tr>
<tr>
<td valign="top">

Varchar



</td>
<td valign="top">

Edm.String



</td>
</tr>
<tr>
<td valign="top">

NVarchar



</td>
<td valign="top">

Edm.String



</td>
</tr>
<tr>
<td valign="top">

Char



</td>
<td valign="top">

Edm.String



</td>
</tr>
<tr>
<td valign="top">

NChar



</td>
<td valign="top">

Edm.String



</td>
</tr>
<tr>
<td valign="top">

Binary



</td>
<td valign="top">

Edm.Binary



</td>
</tr>
<tr>
<td valign="top">

Varbinary



</td>
<td valign="top">

Edm.Binary



</td>
</tr>
</table>



## Example SQL Type Mapping

The following examples shows how SAP HANA SQL types \(name, integer, Varchar\) of columns in a table are mapped to the OData EDM types in the properties of an entity type.

SAP HANA SQL:

```
{name = "ID"; sqlType = INTEGER; nullable = false;},
{name = "RefereeID"; sqlType = VARCHAR; nullable = true;}

```

The following example illustrates how the SAP HANA SQL types illustrated in the previous example are mapped to EDM types:

```
<Property Name="ID" Type="Edm.Int32" Nullable="false"/>
<Property Name="RefereeID" Type="Edm.String" Nullable="true"/>

```

