<!-- loioff3aa12ba90247c8b7c326199d53978a -->

# OData Annotations for Entity-Type Properties

A list of the supported annotations for properties of entity types.



-   [`sap:semantics`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_mcb_5l4_pw)

-   [`sap:parameter`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_jzs_rj4_pw)

-   [`sap:label`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_bll_jj4_pw)

-   [`sap:filterable`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_pwm_z34_pw)

-   [`sap:display-format`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_z5n_v34_pw)

-   [`sap:aggregation-role`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_tn3_hh4_pw)

-   [`sap:unit`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_r5b_hh4_pw)

-   [`sap:filter-restriction`](odata-annotations-for-entity-type-properties-ff3aa12.md#loioff3aa12ba90247c8b7c326199d53978a__section_jww_gh4_pw)




<a name="loioff3aa12ba90247c8b7c326199d53978a__section_mcb_5l4_pw"/>

## sap:semantics

The semantic of the entity-type property.



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The annotation is added only for the properties representing calculated attributes or input parameters in a calculation view. The annotation value corresponds to the semantic type of a calculated attribute or an input parameter. The semantic type of an **input parameter** is specified as a value of “`type`” attribute of “`valueDomain`” element, defined in a calculation view definition file \(for example, `myCalcView.hdbcalculationview`\), as illustrated in the following example:

> ### Sample Code:  
> ```
> <variable id="parameterID" parameter="true">
>     <variableProperties datatype="VARCHAR" mandatory="true">
>         <valueDomain type="Currency"/>
>         ...
>     </variableProperties>
> </variable>
> ```

Semantic type of a **calculated attribute** is specified as a value of a “`semanticType`” attribute of “`calculatedAttribute`” element, defined in a calculation view definition file \(for example, `myCalcView.hdbcalculationview`\), as illustrated in the following example:

> ### Sample Code:  
> ```
> <calculatedAttribute id="attributeID" semanticType="currencyCode">
>     ...
> </calculatedAttribute>
> ```

The following table shows how the semantic type values of calculated attributes and input parameters are mapped to the values of the “`sap:semantics`” annotation:

> ### Restriction:  
> Only those values listed in the following table are supported.

<a name="loioff3aa12ba90247c8b7c326199d53978a__table_ds1_jl4_pw"/>Mapping Between Attribute Values and Annotation


<table>
<tr>
<th valign="top">

Calculated Attribute Semantic Type



</th>
<th valign="top">

Input Parameter Semantic Type



</th>
<th valign="top">

sap:semantics value



</th>
</tr>
<tr>
<td valign="top">

currencyCode



</td>
<td valign="top">

Currency



</td>
<td valign="top">

currency-code



</td>
</tr>
<tr>
<td valign="top">

unitOfMeasure



</td>
<td valign="top">

UnitOfMeasure



</td>
<td valign="top">

unit-of-measure



</td>
</tr>
<tr>
<td valign="top">

date.businessDateFrom



</td>
<td valign="top">

\-



</td>
<td valign="top">

dtstart



</td>
</tr>
<tr>
<td valign="top">

date.businessDateTo



</td>
<td valign="top">

\-



</td>
<td valign="top">

dtend



</td>
</tr>
</table>



<a name="loioff3aa12ba90247c8b7c326199d53978a__section_jzs_rj4_pw"/>

## sap:parameter

A property is annotated with this annotation, if it represents a parameter.



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The annotation is added only to the properties representing input parameters of a calculation view. The annotation value corresponds to the value of the “`mandatory`” attribute in the input parameter definition, defined in a calculation view definition file \(`myCalcView.hdbcalculationview`\).

> ### Sample Code:  
> ```
> <variable id="inputParameterId" parameter="true">
>     <variableProperties datatype="INTEGER" mandatory="true">
> </variable>
> ```

The following table shows how the value of the “`mandatory`” attribute value is mapped to the value of the “`sap:parameter`” annotation:

<a name="loioff3aa12ba90247c8b7c326199d53978a__table_ytt_lk4_pw"/>Mapping Between Attribute Values and Annotation


<table>
<tr>
<th valign="top">

 “mandatory” Attribute Value



</th>
<th valign="top">

sap:parameter Value



</th>
</tr>
<tr>
<td valign="top">

true



</td>
<td valign="top">

mandatory



</td>
</tr>
<tr>
<td valign="top">

false



</td>
<td valign="top">

optional



</td>
</tr>
</table>



<a name="loioff3aa12ba90247c8b7c326199d53978a__section_bll_jj4_pw"/>

## sap:label

A short, human-readable text that is suitable for use in labels and captions in a user interface \(UI\).



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The annotation is added only for the properties representing calculated attributes or input parameters of a calculation view. The annotation value corresponds to the “`defaultDescription`” attribute in the definition of an input parameter or a calculated attribute in the calculation view definition \(`myCalcView.hdbcalculationview`\) file.

> ### Sample Code:  
> ```
> <variable id="inputParameterId" parameter="true">
>     <descriptions defaultDescription="Input parameter label"/>
> </variable>
> 
> <calculatedAttribute id="calcAttributeId">
>     <descriptions defaultDescription="Calculated attribute label"/>
> </calculatedAttribute>
> ```



<a name="loioff3aa12ba90247c8b7c326199d53978a__section_pwm_z34_pw"/>

## sap:filterable

Indicates if the property can be used with the “`$filter`” system query option.



### Default Value

“`true`”



### Additional Supported Values

The annotation is added with the “`false`” value if the property satisfies one of the following conditions:

-   The property represents a generated key

-   The property represents a measure attribute of a calculation view

-   The property is used in the aggregation, defined as the “`aggregates always`” expression in the XS OData service-definition \(`.xsodata`\) file.




<a name="loioff3aa12ba90247c8b7c326199d53978a__section_z5n_v34_pw"/>

## sap:display-format

The format used to display the property.



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The “`Date`” value can be used if the `SQL DATE` type is used for the property on the database side.



<a name="loioff3aa12ba90247c8b7c326199d53978a__section_tn3_hh4_pw"/>

## sap:aggregation-role

The aggregation role of the property.



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The “`measure`” value can be used if the property represents a measure attribute of a calculation view or is used in the aggregation that is defined in the “`aggregates always`” expression in the XS OData service-definition \(`.xsodata`\) file.



<a name="loioff3aa12ba90247c8b7c326199d53978a__section_r5b_hh4_pw"/>

## sap:unit

The name of a property in the context of the entity type containing the currency code or unit of measure for a numeric value of the current property.



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The annotation is added only for the properties representing calculated attributes of a calculation view. The annotation value corresponds to the value of “`attributeName`” attribute of “`unitCurrencyAttribute`” element of the calculated attribute definition in `myCalcView.hdbcalculationview` file.

> ### Note:  
> In the following example, the annotation value will be “`currencyCodeAttribute`”.

> ### Sample Code:  
> ```
> <calculatedAttribute id="attributeId">
>     <unitCurrencyAttribute attributeName="currencyCodeAttribute"/>
> </calculatedAttribute>
> ```



<a name="loioff3aa12ba90247c8b7c326199d53978a__section_jww_gh4_pw"/>

## sap:filter-restriction

Describes filter restrictions for the property, if any exist.



### Default Value

Undefined; there is no defined default value.



### Additional Supported Values

The annotation is added only for the properties representing input parameters of a calculation view. The annotation value corresponds to the values of “`multiLine`” and “`type`” attributes of the “`selection`” element of the input parameter definition in the calculation view definition file \(for example, `myCalcView.hdbcalculationview`.

> ### Sample Code:  
> ```
> <variable id="parameterId" parameter="true">
>     <variableProperties datatype="INTEGER">
>         <selection multiLine="false" type="SingleValue"/>
>     </variableProperties>
> </variable>
> ```

The following table below shows the mapping between the “`multiLine`” and “`type`” attribute values and the value of the “`sap:filter-restriction`” annotation.

> ### Restriction:  
> Only those values specified in the following table are supported.

<a name="loioff3aa12ba90247c8b7c326199d53978a__table_qlb_5h4_pw"/>Mapping Between Attribute Values and Annotation


<table>
<tr>
<th valign="top">

multiLine



</th>
<th valign="top">

type



</th>
<th valign="top">

sap:filter-restriction



</th>
</tr>
<tr>
<td valign="top">

false



</td>
<td valign="top">

SingleValue



</td>
<td valign="top">

single-value



</td>
</tr>
<tr>
<td valign="top">

true



</td>
<td valign="top">

SingleValue



</td>
<td valign="top">

multi-value



</td>
</tr>
<tr>
<td valign="top">

false



</td>
<td valign="top">

Interval



</td>
<td valign="top">

interval



</td>
</tr>
</table>

**Related Information**  


[Enable SAP OData Annotations](enable-sap-odata-annotations-e4fe924.md "Add annotations to the OData v2$metadata document.")

[OData Entity Set Annotations](odata-entity-set-annotations-1b8ebec.md "A list of the attributes that can be used as annotations in the entity set element (edm:EntitySet).")

[OData Entity-Type Annotations](odata-entity-type-annotations-cc55d95.md "A list of the attributes that can be used as annotations in the entity type element (edm:EntityType).")

[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

