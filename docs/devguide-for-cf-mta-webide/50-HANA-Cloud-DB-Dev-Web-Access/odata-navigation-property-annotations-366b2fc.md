<!-- loio366b2fc1e8fe48d79a7bb996c033a09e -->

# OData Navigation Property Annotations

A list of the annotations supported for use with relations between entities.



## Overview

-   [`sap:creatable`](odata-navigation-property-annotations-366b2fc.md#loio366b2fc1e8fe48d79a7bb996c033a09e__section_tz4_4n4_pw)

-   [`sap:filterable`](odata-navigation-property-annotations-366b2fc.md#loio366b2fc1e8fe48d79a7bb996c033a09e__section_nfc_k44_pw)




<a name="loio366b2fc1e8fe48d79a7bb996c033a09e__section_tz4_4n4_pw"/>

## sap:creatable

Indicates if new related entities can be created.



### Default Value

“`true`”



### Additional Supported Values

The annotation value is always “`false`” because neither “`deep insert`” \(`POST` request payload containing data for both parent and related entity\) nor `POST` request for the `.../EntitySet(key)/navPropertyName` URL is supported in XS OData.



<a name="loio366b2fc1e8fe48d79a7bb996c033a09e__section_nfc_k44_pw"/>

## sap:filterable

Indicates if the property can be used with the “`$filter`” system query option.



### Default Value

“`true`”



### Additional Supported Values

The annotation value is always “`false`” because navigation properties cannot be used in a `$filter` system query option in XS OData.

**Related Information**  


[OData Entity Set Annotations](odata-entity-set-annotations-1b8ebec.md "A list of the attributes that can be used as annotations in the entity set element (edm:EntitySet).")

[OData Entity-Type Annotations](odata-entity-type-annotations-cc55d95.md "A list of the attributes that can be used as annotations in the entity type element (edm:EntityType).")

[OData Annotations for Entity-Type Properties](odata-annotations-for-entity-type-properties-ff3aa12.md "A list of the supported annotations for properties of entity types.")

[OData Association Set Annotations](odata-association-set-annotations-571c771.md "A list of the annotations supported for use with relations between association sets.")

[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

