<!-- loio2ec97095dcbd420794670912e3bc9cd6 -->

# OData Parameter Entity Sets

SAP HANA calculation views can interpret input parameters. For OData, these parameters can be entered by using a special parameter *entity set*.

Parameter entity sets can be generated for calculation views by adding *parameters via entity* to the entity, as illustrated in the following service-definition example:

```
service { 
	"sample.odata::calc" as "CalcView"
        keys generate local "ID"
        parameters via entity; 
}  
```

During loading of the service, parameters specified in `sample.odata/calc.calculationview` are retrieved from the metadata of the calculation view and exposed as a new `EntitySet` named after the entity set name and the suffix `Parameters`, for example, `CalcViewParameters`. A `NavigationProperty` named `Results` is generated to retrieve the results from the parameterized call.

The name of the generated parameter entity set and the navigation property can be customized, as illustrated in the following service-definition example:

```
service { 
	"sample.odata::calc" as "CalcView"
        keys generate local "ID"
        parameters via entity "CVParams" results property "Execute"; 
}  
```

With the definition above, the name of the parameter entity set is `CVParams`, and the name of the `NavigationProperty` for the results is `Execute`.



## Navigating to Entities via Parameters

In an OData service definition, you can enable navigation between an entity and a parameterized entity. This feature is particularly useful if you need to have access to individual entries in a parameterized entity set, for example, a calculation view with parameters. If you need to access individual entries in an entity set that has parameters, you must expose the parameters as keys. If you do not need to have access to individual entries in an entity set, you can use the `key generate local` option to generate a pseudo key.

To enable navigation between an entity and a parameterized entity, you must perform the following steps:

1.  Specify the parameters as part of the key of the target entity
2.  Define the association between the entities

Enabling navigation between an entity and a parameterized entity is only possible if the parameters are part of the entity-type key in the OData service definition file. To make the parameters part of the key of the target entity, use the `via key` syntax, as illustrated in the following example:

```
service {
   "sap.test::calcview" key ("theKeyColumns") parameters via key and entity;
}
```

You also have to define an **association** between the source and target entities, for example, with additional entries introduced by the `via parameters` keyword, as illustrated in the following example:

```
service {
   "sap.test::table" as "Tab" navigates ("avp" as "ViewNav");
   "sap.test::calcview" as "View" key ("theKeyColumns") parameters via key and entity;
 
   association via parameters "avp"
     principal "Tab"("paramValue") multiplicity "*"
     dependent "View"("parameter") multiplicity "*";
}
```

> ### Note:  
> The order of the property list of the dependent end is crucial.

The parameters you define in the dependent end of the association **must** be the first properties in the list. In addition, the parameters specified **must** be given in the same order as they are specified in the view, as illustrated in the following example:

```
association via parameters "avp"
   principal "Tab"("col1", "col2", "col3") multiplicity "*"
   dependent "View"("parameter1", "parameter2", "colA") multiplicity "*";
```

In the example immediately above, the principal “`Tab`” has three columns that contain the information that is required to navigate to the dependent “`View`” in the association.

-   “`col1`”

    The value of “`col1`” should be set for “`parameter1`” 

-   “`col2`”

    The value of “`col2`” should be set for “`parameter2`” 

-   “`col3`”

    The parameter “`col3`” contains additional information that is not passed as an input parameter, but as part of a `WHERE` condition.


The generated SQL statement would look like the following:

```
select ... from "sap.test::calcview"(placeholder."$$parameter1$$"=>?, placeholder."$$parameter2$$"=>?) 
                   where "colA"=? 
```

> ### Note:  
> This navigation property cannot be used in combination with the OData query options `$expand`, `$filter` and `$orderby`.

