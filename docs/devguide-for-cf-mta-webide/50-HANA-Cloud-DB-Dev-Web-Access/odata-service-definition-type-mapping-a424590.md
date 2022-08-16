<!-- loioa4245904522543f4b1917eeeae978f78 -->

# OData Service-Definition Type Mapping

During the activation of the OData service definition, SQL types defined in the service definition are mapped to EDM types according to a mapping table.

For example, the SQL type "`Time`" is mapped to the EDM type "`EDM.Time`"; the SQL type "`Decimal`" is mapped to the EDM type "`EDM.Decimal`"; the SQL types "`Real`" and "`Float`" are mapped to the EDM type "`EDM.Single`".

> ### Note:  
> The OData implementation in SAP HANA Extended Application Services \(SAP HANA XS\) does not support all SQL types.

In the following example, the SQL types of columns in a table are mapped to the EDM types in the properties of an entity type.

```
{name = "ID"; sqlType = INTEGER; nullable = false;}, {name = "RefereeID"; sqlType = VARCHAR; nullable = true;}
```

```
<Property Name="ID" Type="Edm.Int32" Nullable="false"/> <Property Name="RefereeID" Type="Edm.String" Nullable="true"/>
```

**Related Information**  


[OData Service Definition: SQL-EDM Type Mapping \(XSOData\)](odata-service-definition-sql-edm-type-mapping-xsodata-db41333.md "During the activation of the OData service definition, the SAP HANA SQL types are mapped to the required OData EDM types according to the rules specified in a mapping table.")

[OData Service Definitions](odata-service-definitions-b8900df.md "The OData service definition defines what data to expose with OData, how, and to whom. Data exposed as an OData collection is available for analysis and display by client applications, for example, a browser that uses functions provided by an OData client library running on the client system.")

