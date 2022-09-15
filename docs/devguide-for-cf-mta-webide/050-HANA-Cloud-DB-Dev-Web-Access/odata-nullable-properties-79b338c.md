<!-- loio79b338c0296c4518b83aa6b19133bba5 -->

# OData Nullable Properties

You can create a service to enable nullable properties in OData.

During the 'Create' phase, the XSODATA layer generates all entity properties automatically. Since the properties are not nullable, consumers of the code are forced to pass dummy values into them. However, OData supports `$filter` and `$orderby` conditions on the `null` value. This means that it is now possible to treat `null` as a value, if you enable it. You can enable this behavior for the entire service only, not per entity.

The following code example provides information about how you can do this.

> ### Sample Code:  
> ```
> service {  
>  …  
>  }  
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

If you enable support for `null`, then `$filter` requests, such as `$filter=NVARCHAR_01 eq null`, are possible. Otherwise `null` is rejected with an exception. If you do not enable the `null` support, then the default behavior applies.

> ### Note:  
> `null` values are “ignored” in comparisons: "ignored" in the sens that if you compare a column with `null` and the columns contain per definition no `null` values, no record passes the filter.

**Related Information**  


[OData Configurable Cache Settings](odata-configurable-cache-settings-a5d3bea.md "You can create a service to configure the cache settings for the $metadata request to optimize performance.")

[OData Hints for SQL Select Statements](odata-hints-for-sql-select-statements-34c4b42.md "Provide specific hints for SQL select statements in your OData service.")

[OData Entity Limits](odata-entity-limits-b6efb15.md "Restrict the amount of entities that an OData service can load from the database.")

