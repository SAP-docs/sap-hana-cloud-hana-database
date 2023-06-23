<!-- loio1b8ebecb14594203bd50fa227797c890 -->

# OData Entity Set Annotations

A list of the attributes that can be used as annotations in the entity **set** element \(`edm:EntitySet`\).



For XS OData services, entity sets can be annotated with the following attributes:

-   [`sap:addressable`](odata-entity-set-annotations-1b8ebec.md#loio1b8ebecb14594203bd50fa227797c890__section_yn2_rvn_pw)

    Direct access to the specified entity set is permitted

-   [`sap:creatable`](odata-entity-set-annotations-1b8ebec.md#loio1b8ebecb14594203bd50fa227797c890__section_bvk_rvn_pw)

    New entities can be created in the specified entity set

-   [`sap:updatable`](odata-entity-set-annotations-1b8ebec.md#loio1b8ebecb14594203bd50fa227797c890__section_t24_rvn_pw)

    Existing entities in the specified entity set can be updated

-   [`sap:deletable`](odata-entity-set-annotations-1b8ebec.md#loio1b8ebecb14594203bd50fa227797c890__section_vbv_rvn_pw)

    Existing entities can be removed from the specified entity set




<a name="loio1b8ebecb14594203bd50fa227797c890__section_yn2_rvn_pw"/>

## sap:addressable

Permit direct access to the specified entity set.



### Default Value

“true”



### Additional Supported Values

“false” if the entity set represents either a calculation view or input parameters for a calculation view.



<a name="loio1b8ebecb14594203bd50fa227797c890__section_bvk_rvn_pw"/>

## sap:creatable

Allow the creation of new entities in the specified entity set.



### Default Value

“true”



### Additional Supported Values

The following table shows the additional values that are supported for the attribute `sap:creatable` in the `edm:EntitySet` element and the corresponding requirements.

**Additional Supported Values**


<table>
<tr>
<th valign="top">

Parameter Value



</th>
<th valign="top">

Requirement



</th>
</tr>
<tr>
<td valign="top" rowspan="4">

 “false” 



</td>
<td valign="top">

The "`create forbidden`" setting is defined for the entity set in the OData service definition \(`.xsodata`\) file



</td>
</tr>
<tr>
<td valign="top">

The entity set represents a database view, for example, a table or a calculation view.



</td>
</tr>
<tr>
<td valign="top">

The entity set represents input parameters for a calculation view.



</td>
</tr>
<tr>
<td valign="top">

 “`aggregation`” is defined for the entity set, for example, using the “`aggregates always`” expression in the OData service definition \(`.xsodata`\) file.



</td>
</tr>
</table>



<a name="loio1b8ebecb14594203bd50fa227797c890__section_t24_rvn_pw"/>

## sap:updatable

Allow changes and updates to existing entities in the specified entity set.



### Default Value

“true”



### Additional Supported Values

The following table shows the additional values that are supported for the attribute `sap:updatable` in the `edm:EntitySet` element and the corresponding requirements.

**Additional Supported Values**


<table>
<tr>
<th valign="top">

Parameter Value



</th>
<th valign="top">

Requirement



</th>
</tr>
<tr>
<td valign="top" rowspan="5">

 “false” 



</td>
<td valign="top">

The "`update forbidden`" setting is defined for the entity set in the OData service definition \(`.xsodata`\) file



</td>
</tr>
<tr>
<td valign="top">

The entity set represents a database view, for example, a table or a calculation view.



</td>
</tr>
<tr>
<td valign="top">

The entity set represents input parameters for a calculation view.



</td>
</tr>
<tr>
<td valign="top">

 “`aggregation`” is defined for the entity set, for example, using the “`aggregates always`” expression in the OData service definition \(`.xsodata`\) file.



</td>
</tr>
<tr>
<td valign="top">

A generated key is defined for the entity set.



</td>
</tr>
</table>



<a name="loio1b8ebecb14594203bd50fa227797c890__section_vbv_rvn_pw"/>

## sap:deletable

Allow the deletion of entities from the specified entity set.



### Default Value

“true”



### Additional Supported Values

The following table shows the additional values that are supported for the attribute `sap:deletable` in the `edm:EntitySet` element and the corresponding requirements.

**Additional Supported Values**


<table>
<tr>
<th valign="top">

Parameter Value



</th>
<th valign="top">

Requirement



</th>
</tr>
<tr>
<td valign="top" rowspan="5">

 “false” 



</td>
<td valign="top">

The "`delete forbidden`" setting is defined for the entity set in the OData service definition \(`.xsodata`\) file



</td>
</tr>
<tr>
<td valign="top">

The entity set represents a database view, for example, a table or a calculation view.



</td>
</tr>
<tr>
<td valign="top">

The entity set represents input parameters for a calculation view.



</td>
</tr>
<tr>
<td valign="top">

 “`aggregation`” is defined for the entity set, for example, using the “`aggregates always`” expression in the OData service definition \(`.xsodata`\) file.



</td>
</tr>
<tr>
<td valign="top">

A generated key is defined for the entity set.



</td>
</tr>
</table>

**Related Information**  


[SAP OData Annotations](sap-odata-annotations-b7fb60b.md "The OData v2 protocol allows the use of annotations in the metadata document.")

[Enable SAP OData Annotations](enable-sap-odata-annotations-e4fe924.md "Add annotations to the OData v2$metadata document.")

[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

