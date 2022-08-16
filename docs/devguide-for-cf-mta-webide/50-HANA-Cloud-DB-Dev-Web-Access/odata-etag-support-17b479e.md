<!-- loio17b479e1e928465baa07a5688fd5e355 -->

# OData ETag Support

This feature allows a service to define the fields that are to be included in the concurrency check.

You can now use entity tags \(ETags\) for optimistic concurrency control. If you choose to use this feature, then you must enable it per entity in the `.xsodata` file. Enabling this feature per entity allows for the concurrency control to be applied to multiple fields. The following code example provides information about how to do this.

> ### Sample Code:  
> ```
> service
> { entity "sap.test.odata.db.views::Etag" as "EtagAll"
>   key ("KEY_00") concurrencytoken;
>  entity "sap.test.odata.db.views::Etag" as "EtagNvarchar"
>   key ("KEY_00") concurrencytoken ("NVARCHAR_01","INTEGER_03");
> }
> ```

If you specify `concurrencytoken` only, then all properties, except the key properties, are used to calculate the ETag value. If you provide specific properties, then only those properties are used for the calculation.

> ### Note:  
> You **cannot** specify `concurrencytoken` on aggregated properties that use the `AVG` \(average\) aggregation method.

