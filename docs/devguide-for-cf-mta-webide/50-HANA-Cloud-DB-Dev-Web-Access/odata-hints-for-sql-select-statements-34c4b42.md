<!-- loio34c4b422010c45a795362d8ac6a32638 -->

# OData Hints for SQL Select Statements

Provide specific hints for SQL select statements in your OData service.

You can use the `hints` property to add elements to the SQL `SELECT` statement the OData service uses to query data.

> ### Caution:  
> Bear in mind that setting the wrong hint can result in unexpected data results. And if you remove the \(default\) `NO_CALC_VIEW_UNFOLDING` hint explicitly \(for example, to improve performance\), it is important to check the results of the resulting calculation views for accuracy and correctness.

> ### Sample Code:  
> OData Service Hints Settings
> 
> ```
> service {  
>  …  
> }  
> settings {  
>   support null; 
>   content cache-control "no-store"; 
>   metadata cache-control "max-age=86401,must-revalidate"; 
>   hints 
>       "NO_CALC_VIEW_UNFOLDING", "ABC"; 
>   limits 
>       max_records = 10, 
>       max_expanded_records = 30; 
> }
> ```

If no `hints` are specified, the default hint '`NO_CALC_VIEW_UNFOLDING`' is still added to the SQL `SELECT` statements used in the service query, for example, `select * from with hint (NO_CALC_VIEW_UNFOLDING)`. This is the default behavior and is required for backward compatibility.

If SQL hints are specified, for example, '`hints null`' or any other value such as '`hints ABC`', then the SQL parameter '`NO_CALC_VIEW_UNFOLDING`' is **not** added to the SQL `SELECT` statement automatically. For '`hints null`', no hint statement is included in the SQL `SELECT` statement used by the OData service.

> ### Tip:  
> It is possible to add the hint `"NO_CALC_VIEW_UNFOLDING"` manually, and multiple hints can be added by separating each hint with a comma. For example, the setting '`hints "NO_CALC_VIEW_UNFOLDING", "ABC"`' produces the SQL statement '`select * from with hint (NO_CALC_VIEW_UNFOLDING, ABC)`'.

**Related Information**  


[OData Nullable Properties](odata-nullable-properties-79b338c.md "You can create a service to enable nullable properties in OData.")

[OData Configurable Cache Settings](odata-configurable-cache-settings-a5d3bea.md "You can create a service to configure the cache settings for the $metadata request to optimize performance.")

[OData Entity Limits](odata-entity-limits-b6efb15.md "Restrict the amount of entities that an OData service can load from the database.")

