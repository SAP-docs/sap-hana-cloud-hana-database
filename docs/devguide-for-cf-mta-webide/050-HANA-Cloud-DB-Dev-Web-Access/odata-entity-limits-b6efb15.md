<!-- loiob6efb153ac8a4b96bb48baa14aa3e358 -->

# OData Entity Limits

Restrict the amount of entities that an OData service can load from the database.

You can use the `limits` property in `settings` to restrict the amount of entities loaded from the database by an OData service. The `limits` setting is useful if you need to avoid problems with memory shortages and want to reduce the size of the data included in the response to an OData service query.

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
>       "NO_CALC_VIEW_UNFOLDING"; 
>   limits 
>       max_records = 10, 
>       max_expanded_records = 30; 
> }
> ```



<a name="loiob6efb153ac8a4b96bb48baa14aa3e358__section_y4j_1y5_cfb"/>

## max\_records

You can use the property `max_records` to restrict the number of entities addressed by the resource path. If there are more records selected than allowed with `max_records` then an error \(400 Bad request\) is returned to the client. To avoid the problem of bad requests, the client can use `$top` and `$skip` to select less than the number of entities specified in `max_records`.

> ### Note:  
> The default value for `max_records` is “1000”. If this value is **not** suitable for your application, add the appropriate setting to the application's xsodata service file, for example, `max_records = 25;`.



<a name="loiob6efb153ac8a4b96bb48baa14aa3e358__section_mdg_by5_cfb"/>

## max\_expanded\_records

You can use `max_expanded_records` to restrict the number of entries of a single expanded navigation property. If there are more records selected than allowed with `max_expanded_records`, then an error \(400 Bad request\) is returned to the client. With OData V2 its not possible to apply `$top` or `$skip` to an expanded navigation property, which means that the client cannot avoid this error alone solely for the expanded navigation property.

However, if a feed is returned then reducing the entries in the feed with `$top` and `$skip` or `$filter` might help to reduce the number of entries collected with expanded navigation properties. Bear in mind that expanded records are counted per navigation property and level, so for `max_expanded_records = 100`, there may be 1 root entity with 100 expanded items or, alternatively, 2 root entities one of which has 25 and the other 75 expanded items.

> ### Note:  
> The default value for `max_expanded_records` is “10000”. If this value is **not** suitable for your application, add the appropriate setting to the applications xsodata service file, for example, `max_expanded_records = 250;`.

**Related Information**  


[OData Nullable Properties](odata-nullable-properties-79b338c.md "You can create a service to enable nullable properties in OData.")

[OData Configurable Cache Settings](odata-configurable-cache-settings-a5d3bea.md "You can create a service to configure the cache settings for the $metadata request to optimize performance.")

[OData Hints for SQL Select Statements](odata-hints-for-sql-select-statements-34c4b42.md "Provide specific hints for SQL select statements in your OData service.")

