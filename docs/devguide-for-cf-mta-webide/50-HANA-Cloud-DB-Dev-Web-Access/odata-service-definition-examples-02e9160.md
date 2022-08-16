<!-- loio02e91608eb174dcea6d544aad6ea2e12 -->

# OData Service-Definition Examples

The OData service definition describes how data exposed in an end point can be accessed by clients using the OData protocol.

Each of the examples listed below is explained in a separate section. The examples show how to use the OData Service Definition Language \(OSDL\) in the OData service-definition file to generate an operational OData service that enables clients to access the OData end point you set up.

-   Empty Service
-   Namespace Definition
-   Object Exposure
-   Property Projection
-   Key Specification
-   Associations
-   Aggregation
-   Parameter Entity Sets
-   Nullable Properties

> ### Restriction:  
> OData supports both the ATOM and JSON formats in request and response payloads. However, the Node.js module only support JSON. To specify JSON as the payload format, you can either add the following system-query option to the request “`$format=json`” or add the following request header “`Accept:json`”.

**Related Information**  


[OData Empty Service](odata-empty-service-51d401d.md)

[OData Namespace Definition](odata-namespace-definition-f9f5f22.md)

[OData Object Exposure](odata-object-exposure-d08f928.md)

[OData Property Projection](odata-property-projection-471609f.md)

[OData Key Specification](odata-key-specification-e86a01a.md "The OData specification requires an EntityType to denote a set properties forming a unique key. In HANA only tables may have a unique key, the primary key. For all other (mostly view) objects you need to specify a key for the entity.")

[OData Associations](odata-associations-595f0a1.md)

[OData Aggregation](odata-aggregation-64560b8.md)

[OData Parameter Entity Sets](odata-parameter-entity-sets-2ec9709.md)

[OData ETag Support](odata-etag-support-17b479e.md "This feature allows a service to define the fields that are to be included in the concurrency check.")

[OData Nullable Properties](odata-nullable-properties-79b338c.md "You can create a service to enable nullable properties in OData.")

[OData Configurable Cache Settings](odata-configurable-cache-settings-a5d3bea.md "You can create a service to configure the cache settings for the $metadata request to optimize performance.")

[Custom Exits for OData Requests](custom-exits-for-odata-requests-0373514.md "Define validation checks or modification operations during an XS OData write request.")

