<!-- loiob79fda306ef84f098f9ddfac772438eb -->

# JSON Documents

JSON documents are stored in the JSON Document Store \(DocStore\) and grouped into JSON collections.

A JSON document contains data described according to the JavaScript Object Notation syntax, which is a text-based, human-readable, data-interchange format.

The source data for a JSON document is stored as an array of comma-separated name-value pairs, and multiple JSON documents can be defined in a single CSV file. In the CSV file, each line represents a single JSON document, and the line-break character \(not a comma\) is used to define the end of one JSON document and the start of the next, as illustrated in the following example:

> ### Sample Code:  
> JSON Documents in a CSV File `myJSONData.csv`
> 
> ```
> {"name": 'Peter', "address": {"street": 'Main Road', "number": 10, "city": 'Heidelberg'} } \n
> {"name": 'Kwame', "address": {"street": 'Independence Avenue', "number": 1957, "city": 'Kumasi'} } \n
> {"name": 'Daijiro', "address": {"street": 'Kawasaki Road', "number": 101, "city": 'Yokohama'} }
> ```

> ### Tip:  
> The line-break is automatically added by your text editor; it is not necessary to add the line-break character \(`\n`\) to the CSV file manually. For more information about importing JSON documents into a document collection in the SAP HANA DocStore, see *Related Information* below.

The content of a JSON document can be specified in nested structures. Unlike XML, however, a JSON document does not have a schema, which means that any valid JSON data can be inserted without first declaring its structure.

> ### Sample Code:  
> JSON Nested Content
> 
> ```json
> { 
>   "author": { 
>       "address": { 
>           "street": "Main Road", 
>           "number": 10,
>           "city": 'Heidelberg' 
>           }, 
>           ... 
>       }, 
>       ... 
>   } 
> ```

To access the information in the nested structure defined in the JSON document, you can use the “dot notation” to define the path to the required value, for example: `"author"."address"."street"`

In a JSON document, it is also possible to define elements in an array, such as the one illustrated in `"addresses": [...]` in the following simple example:

> ### Sample Code:  
> JSON Nested Content
> 
> ```json
> { 
>   "author": { 
>       "addresses": [{ 
>           "street": "First Street" 
>           },{ 
>           "street": "Second Street" 
>           } ]
>       }, 
>       ... 
>   } 
> ```

To enable access to elements defined in an array, a standard index operator `[#]` is required. The index positions start at “1”, which means the first element has the position 1. So, to access the value defined in the **second** address in the example above \(<code>“Second Street”</code>\), you would use something like the following example: `"author"."addresses"[2]."street"`

> ### Tip:  
> This notation can be used anywhere where it is necessary to access a value, for example, “Sort”, “Filter”, “Projection”. If no value exists in the document for a given identifier a NULL value is returned instead.

**Related Information**  


[JSON Collections](json-collections-66a8d33.md "JSON documents are grouped together as “collections ” that are stored in the SAP HANA Documentation Store (DocStore).")

[The SAP HANA JSON Document Store](the-sap-hana-json-document-store-3872240.md "The SAP HANA Document Store contains JSON artifacts grouped in collections.")

[Import JSON Documents into a Document-Store Collection](import-json-documents-into-a-document-store-collection-cf46dc4.md "Import JSON data from a CSV file into a collection in the SAP HANA Document Store.")

[SAP HANA Cloud, SAP HANA Database JSON Document Store Guide](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/2024_1_QRC/en-US/dca379e9c94940e998d9d4b5c656d1bd.html "This guide explains the SAP HANA JSON Document Store.") :arrow_upper_right:

