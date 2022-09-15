<!-- loioa5d3bea8a6ae43779ffaaae925554d0b -->

# OData Configurable Cache Settings

You can create a service to configure the cache settings for the `$metadata` request to optimize performance.

When calling OData services, the services make repeated requests for the `$metadata` document. Since changes to the underlying entity definitions occurs rarely, SAP has enabled the option to configure caching for these `$metadata` documents. By configuring the cache, you can avoid many redundant queries to process the metadata.

The following code example provides information about how you can do this.

> ### Sample Code:  
> ```
> service {
>  ...
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



<a name="loioa5d3bea8a6ae43779ffaaae925554d0b__section_cfq_xtb_dfb"/>

## content cache-control

You can use the `content cache-control` parameter to set the HTTP header "value" that is used for cache control in the data responses, for example:

```
content cache-control "no-store";
```

The value you specify must be enclosed in double quotes \(for example, "*<value\>*"\), and multiple parameters must be separated by a comma.

> ### Tip:  
> You can include any value supported by the HTTP specification for cache-control. `"no-store"` indicates that the cache should not store any details of the client request or server response.



<a name="loioa5d3bea8a6ae43779ffaaae925554d0b__section_ry2_c5b_dfb"/>

## metadata cache-control

You can use the `metadata cache-control` parameter to set the header HTTP "value" that is used for the cache control in the metadata response, for example:

```
metadata cache-control "max-age=86401,must-revalidate";
```

The value you specify for `metadata cache-control` must be enclosed in double quotes \(for example, "*<value\>*"\), and multiple elements must be separated by a comma, as illustrated in the example above.

> ### Tip:  
> You can include any value supported by the HTTP specification for cache-control. In the example, above, `"must-revalidate"` indicates that the cache must verify the status of resources \(fresh or stale\) and not use any stale resource whose validity has expired; `"max-age"` specifies the amount of time a resource is considered fresh \(and still usable\).

**Related Information**  


[OData Nullable Properties](odata-nullable-properties-79b338c.md "You can create a service to enable nullable properties in OData.")

[OData Hints for SQL Select Statements](odata-hints-for-sql-select-statements-34c4b42.md "Provide specific hints for SQL select statements in your OData service.")

[OData Entity Limits](odata-entity-limits-b6efb15.md "Restrict the amount of entities that an OData service can load from the database.")

