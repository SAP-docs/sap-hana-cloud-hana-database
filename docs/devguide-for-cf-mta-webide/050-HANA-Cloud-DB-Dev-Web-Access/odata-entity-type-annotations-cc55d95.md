<!-- loiocc55d955a38e43db93bf026547e93b90 -->

# OData Entity-Type Annotations

A list of the attributes that can be used as annotations in the entity **type** element \(`edm:EntityType`\).



## sap:semantics

Describes the semantic of the entity type.



### Default Value

Undefined.



### Additional Supported Values

The following values are supported, in addition to the default value \(if defined\):

-   `"aggregate"` value in one of the following cases:

    -   Where aggregation is defined for the entity set of the entity type using `"aggregates"` expression in `.xsodata` file

    -   Where the entity type represents a calculation view, which has a measure attribute


-   `"parameters"` value if the entity type represents input parameters for a calculation view


**Related Information**  


[OData Entity Set Annotations](odata-entity-set-annotations-1b8ebec.md "A list of the attributes that can be used as annotations in the entity set element (edm:EntitySet).")

[Enable SAP OData Annotations](enable-sap-odata-annotations-e4fe924.md "Add annotations to the OData v2$metadata document.")

[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

