<!-- loio64560b807f004d8189b94385e5d02f1e -->

# OData Aggregation

The results of aggregations on columns change dynamically depending on the grouping conditions. This means that aggregation cannot be performed in SQL views; it needs to be specified in the OData service definition itself. Depending on the type of object to expose, you need to explicitly specify the columns to aggregate and the function to use or derived them from metadata in the database.

In general, aggregations do not have consequences for the metadata document. It just effects the semantics of the concerning properties during runtime. The grouping condition for the aggregation contain all selected non-aggregated properties. Furthermore, aggregated columns cannot be used in `$filter`, and aggregation is only possible with generated keys.



<a name="loio64560b807f004d8189b94385e5d02f1e__section_N1001D_N1000E_N10001"/>

## Derived Aggregation

The simplest way to define aggregations of columns in an object is to derive this information from metadata in the database. The only objects with this information are calculation views and analytic views. For all other object types, for example, tables and SQL views, the activation will not work. To cause the service to use derived information, you must specify the keywords *aggregates always*, as illustrated in the following example:

```
service { 
	"sample.odata::calc" as "CalcView"
        keys generate local "ID"
        aggregates always; 
}  
```



<a name="loio64560b807f004d8189b94385e5d02f1e__section_N10033_N1000E_N10001"/>

## Explicit Aggregation

The example for the explicit aggregation is based on the following table definition: `sample.odata:revenues.hdbtable`

```
COLUMN TABLE "sample.odata::revenues" (
	"Month" INTEGER NOT NULL,
	"Year" INTEGER NOT NULL,
	"Amount" INTEGER,
	PRIMARY KEY ("Month","Year")
); 
```

You can aggregate the columns of objects \(without metadata\) that are necessary for the derivation of aggregation by explicitly denoting the column names and the functions to use, as illustrated in the following example of a service definition: `sample.odata:aggrexpl.xsodata`

```
service { 
	"sample.odata::revenues" as "Revenues" 
        keys generate local "ID"
        aggregates always (SUM of "Amount"); 
}  
```

The results of the entity set `Revenues` always contain the aggregated value of the column `Amount`. To extract the aggregated revenue amount per year, add `$select=Year,Amount` to your requested URI.

