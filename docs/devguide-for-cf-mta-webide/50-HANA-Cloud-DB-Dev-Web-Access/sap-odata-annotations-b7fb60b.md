<!-- loiob7fb60b91ee54a75bb03e54af1316229 -->

# SAP OData Annotations

The OData v2 protocol allows the use of annotations in the metadata document.

The second version of the OData protocol allows you to add annotations to the metadata document; the purpose of the annotations is to add information and hints to the EDM elements. This structural metadata makes it easy to understand a service, and human-readable documentation can be directly embedded into the metadata document, helping developers consume an OData service. The added information can be used by the service clients \(for example, and SAPUI5 application\) to better represent the service entities. The annotations are divided into annotation elements and annotation attributes, represented as XML elements and XML attributes respectively.

Located at the OData service root, the service document lists the top-level resources that are available. The metadata document, on the other hand, describes the structure of all resources in the OData service; the metadata document is located at the address `$metadata` relative to the OData service root.

The OData protocol defines the concept of the annotations without adding any details concerning the particular names and values, which can or should be used for them. In addition, SAP defines its own specific set of annotations.

> ### Note:  
> Not all of the SAP OData annotations are supported in XS OData. For more information, see *SAP Annotations for OData Version 2.0* in *Related Links* below.

By default, the annotations are **not** serialized in the `$metadata` document of an XS OData service. For each of the annotations a default value is defined according to the information provided in *SAP Annotations for OData Version 2.0*. It is important to remember that an annotation is added to the `metadata` document only if the annotation's value differs from the default value.

To enable the annotations for a particular XS OData service, the following configuration has to be specified in the service document \(the respective `.xsodata` service-definition file\), as illustrated in the following example:

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

If annotations are enabled for an XS OData service, the following XML name space is added for the `Edmx` element of the `metadata` document:

> ### Sample Code:  
> ```
> xmlns:sap="http://www.sap.com/Protocols/SAPData"
> 
> ```

**Related Information**  


[SAP Annotations for OData Version 2.0](https://scn.sap.com/docs/DOC-44986)

[Enable SAP OData Annotations](enable-sap-odata-annotations-e4fe924.md "Add annotations to the OData v2$metadata document.")

