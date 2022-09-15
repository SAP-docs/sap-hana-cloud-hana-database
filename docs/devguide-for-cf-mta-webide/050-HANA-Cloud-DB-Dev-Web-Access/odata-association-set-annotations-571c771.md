<!-- loio571c7716e0754ba6888c58b11fae2592 -->

# OData Association Set Annotations

A list of the annotations supported for use with relations between association sets.



## Overview

-   [`sap:creatable`](odata-association-set-annotations-571c771.md#loio571c7716e0754ba6888c58b11fae2592__section_bvk_rvn_pw)

-   [`sap:updatable`](odata-association-set-annotations-571c771.md#loio571c7716e0754ba6888c58b11fae2592__section_t24_rvn_pw)

-   [`sap:deletable`](odata-association-set-annotations-571c771.md#loio571c7716e0754ba6888c58b11fae2592__section_vbv_rvn_pw)




<a name="loio571c7716e0754ba6888c58b11fae2592__section_bvk_rvn_pw"/>

## sap:creatable

Allow the creation of relations represented by the association set.



### Default Value

“true”



### Additional Supported Values

“`false`” if the association set connects entity sets for calculation view results and calculation view input parameters.



<a name="loio571c7716e0754ba6888c58b11fae2592__section_t24_rvn_pw"/>

## sap:updatable

Allow changes and updates to relations represented by the association set.



### Default Value

“true”



### Additional Supported Values

“`false`” if the association set connects entity sets for calculation view results and calculation view input parameters.



<a name="loio571c7716e0754ba6888c58b11fae2592__section_vbv_rvn_pw"/>

## sap:deletable

Allow the deletion of relations represented by the association set.



### Default Value

“true”



### Additional Supported Values

“`false`” if the association set connects entity sets for calculation view results and calculation view input parameters.

**Related Information**  


[OData Entity Set Annotations](odata-entity-set-annotations-1b8ebec.md "A list of the attributes that can be used as annotations in the entity set element (edm:EntitySet).")

[OData Entity-Type Annotations](odata-entity-type-annotations-cc55d95.md "A list of the attributes that can be used as annotations in the entity type element (edm:EntityType).")

[OData Annotations for Entity-Type Properties](odata-annotations-for-entity-type-properties-ff3aa12.md "A list of the supported annotations for properties of entity types.")

[OData Navigation Property Annotations](odata-navigation-property-annotations-366b2fc.md "A list of the annotations supported for use with relations between entities.")

[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

