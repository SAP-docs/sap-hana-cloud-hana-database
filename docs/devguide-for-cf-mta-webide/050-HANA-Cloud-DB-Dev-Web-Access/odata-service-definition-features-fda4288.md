<!-- loiofda42888439142dc9984d3560bc68206 -->

# OData Service-Definition Features

The OData service definition provides a list of keywords that you use in the OData service-definition file to enable important features. For example, the following list illustrates the most-commonly used features used in an OData service-definition and, where appropriate, indicates the keyword to use to enable the feature:

-   **Aggregation**

    The results of aggregations on columns change dynamically, depending on the grouping conditions. As a result, aggregation cannot be done in SQL views; it needs to be specified in the OData service definition itself. Depending on the type of object you want to expose with OData, the columns to aggregate and the function used must be specified explicitly \(**explicit aggregation**\) or derived from metadata in the database \(**derived aggregation**\). Note that aggregated columns cannot be used in combination with the `$filter` query parameter, and aggregation is only possible with generated keys.

-   **Association**

    Define associations between entities to express relationships between entities. With associations it is possible to reflect foreign key constraints on database tables, hierarchies and other relations between database objects.

-   **Key Specification**

    The OData specification requires an EntityType to denote a set of properties forming a unique key. In SAP HANA, only tables can have a unique key, the primary key. All other \(mostly view\) objects require you to specify a key for the entity. The OData service definition language \(OSDL\) enables you to do this by denoting a set of existing columns or by generating a **local key**. Bear in mind that local keys are transient; they exist only for the duration of the current session and cannot be dereferenced.

    > ### Note:  
    > OSDL is the language used to define a service definition; the language includes a list of keywords that you use in the OData service-definition file to enable the required features.

-   **Parameter Entity Sets**

    You can use a special parameter entity set to enter input parameters for SAP HANA calculation views and analytic views. During activation of the entity set, the specified parameters are retrieved from the metadata of the calculation \(or analytical\) view and exposed as a new **EntitySet** with the name suffix "`Parameters`", for example "`CalcViewParameters`".

-   **Projection**

    If the object you want to expose with an OData service has more columns than you actually want to expose, you can use SQL views to restrict the number of selected columns in the `SELECT`. However, for those cases where SQL views are not appropriate, you can use the **with** or **without** keywords in the OData service definition to **include** or **exclude** a list of columns.


**Related Information**  


[OData Service-Definition Examples](odata-service-definition-examples-02e9160.md "The OData service definition describes how data exposed in an end point can be accessed by clients using the OData protocol.")

