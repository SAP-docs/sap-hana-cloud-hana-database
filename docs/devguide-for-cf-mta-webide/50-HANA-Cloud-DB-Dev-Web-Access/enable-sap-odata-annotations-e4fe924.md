<!-- loioe4fe9246773e4cc9958f35e2c8649641 -->

# Enable SAP OData Annotations

Add annotations to the OData v2`$metadata` document.



## Context

Version two of the OData protocol allows you to add annotations to the `$metadata` document. The purpose of the annotations is to add information and hints to the EDM elements; the additional information can be used by the service clients \(for example, an SAPUI5 application\) to more clearly represent the service entities.

> ### Note:  
> SAP defines its own specific set of OData annotations. However, not all of the SAP OData annotations are supported in the XS OData model. For more information, see *SAP OData Annotations* in *Related Links* below.



## Procedure

1.  Open the OData service description, for example, `myODataService.xsodata`.

2.  Enable OData annotations.

    Use the `annotations {}` keyword to enable OData annotations, as illustrated in the following example:

    > ### Sample Code:  
    > Enabling OData Annotations
    > 
    > ```
    > service ... {
    >     ...
    > }
    > annotations {
    >    enable OData4SAP;
    > }
    > 
    > ```

    > ### Restriction:  
    > The annotation configuration must be specified immediately after the “`service`” element.

    If annotations are enabled for an XS OData service, the following XML name space is added for the `Edmx` element of the `$metadata` document:

    > ### Sample Code:  
    > ```
    > xmlns:sap="http://www.sap.com/Protocols/SAPData"
    > 
    > ```


**Related Information**  


[SAP OData Annotations](sap-odata-annotations-b7fb60b.md "The OData v2 protocol allows the use of annotations in the metadata document.")

[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

