<!-- loio03735142bfd647c2a016fcd9359f3348 -->

# Custom Exits for OData Requests

Define validation checks or modification operations during an XS OData write request.

The xsodata library supports custom exits to enable the application to define JavaScript functions which are called while processing the OData request. These exits can be implemented either as a JavaScript function or as a stored procedure. You can define exits for creating, updating, and deleting entity sets as well as for the database commit operation \(for example, pre-commit and post-commit\). It is not possible to define an exit for simple read requests.

> ### Sample Code:  
> Exit definition in the xsodata Service-Definition file
> 
> ```
> 
> service { 
>   "my_name_space::customers" as "Customers" 
>      keys("CustomerID")  
>      navigates("CustomerToProduct" as "Product" from principal)  
>      create forbidden  
>      update using "sap.abc.xyz:myExits.xsjslib::updateEntity"  
>        events( before "sap.abc.xyz:myLoggingInfrastructure.xsjslib::log" )  
>      delete forbidden;  
> } 
> ```



<a name="loio03735142bfd647c2a016fcd9359f3348__section_wbg_qm3_5z"/>

## Exit Types

The following type of write exits are supported for OData write requests in SAP HANA XS:

-   Validation Exit:

    Validation exits allow the application to validate data either before or after the data is changed in the database. Any error returned from the application exit function stops any further processing of the request and a rollback is performed. For batch requests, the processing of further requests in the same change set is stopped.

-   Modification Exit

    Modification exits enable you to define custom logic that can be used to create, update, or delete an entry in an entity set. If defined, a modification exit is is executed instead of the generic actions provided by the OData infrastructure. You use the `using` keyword to register the exit.


**XS OData Validation Exits**


<table>
<tr>
<th valign="top">

Write Request



</th>
<th valign="top">

Code Example



</th>
<th valign="top">

Explanation



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

Create



</td>
<td valign="top">

 <code>create events (before "<i class="varname">&lt;custom exit 1&gt;</i>", after "<i class="varname">&lt;custom exit 2&gt;</i>", ...)</code> 



</td>
<td valign="top">

The xsodata library calls the exit custom exit 1 before creating the entity, and the exit custom exit 2 after creating the entity



</td>
</tr>
<tr>
<td valign="top">

 <code>create events (precommit "<i class="varname">&lt;custom exit 1&gt;</i>", postcommit "<i class="varname">&lt;custom exit 2&gt;</i>", ...)</code> 



</td>
<td valign="top">

The xsodata library calls the exit custom exit 1 before committing the data, and the exit custom exit 2 after committing



</td>
</tr>
<tr>
<td valign="top">

 `create forbidden` 



</td>
<td valign="top">

Prohibits any create operation on the entity set



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Update



</td>
<td valign="top">

 <code>update events (before "<i class="varname">&lt;custom exit 1&gt;</i>", after "<i class="varname">&lt;custom exit 2&gt;</i>", ...)</code> 



</td>
<td valign="top">

The xsodata library calls the exit custom exit 1 before creating the entity, and the exit custom exit 2 after updating the entity



</td>
</tr>
<tr>
<td valign="top">

 <code>update events (precommit "<i class="varname">&lt;custom exit 1&gt;</i>", postcommit "<i class="varname">&lt;custom exit 2&gt;</i>", ...)</code> 



</td>
<td valign="top">

The xsodata library calls the exit custom exit 1 before committing the data, and the exit custom exit 2 after committing



</td>
</tr>
<tr>
<td valign="top">

 `update forbidden` 



</td>
<td valign="top">

Prohibits any update operation on the entity set



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Delete



</td>
<td valign="top">

 <code>delete events (before "<i class="varname">&lt;custom exit 1&gt;</i>", after "<i class="varname">&lt;custom exit 2&gt;</i>", ...)</code> 



</td>
<td valign="top">

The xsodata library calls the exit custom exit 1 before creating the entity, and the exit custom exit 2 after deleting the entity



</td>
</tr>
<tr>
<td valign="top">

 <code>delete events (precommit "<i class="varname">&lt;custom exit 1&gt;</i>", postcommit "<i class="varname">&lt;custom exit 2&gt;</i>", ...)</code> 



</td>
<td valign="top">

The xsodata library calls the exit custom exit 1 before committing the data, and the exit custom exit 2 after committing



</td>
</tr>
<tr>
<td valign="top">

 `delete forbidden` 



</td>
<td valign="top">

Prohibits the deletion of the entity



</td>
</tr>
</table>

The following table lists the types of modification exits you can define with XS Odata:

**XS OData Modification Exits**


<table>
<tr>
<th valign="top">

Write Request



</th>
<th valign="top">

Code Example



</th>
<th valign="top">

Explanation



</th>
</tr>
<tr>
<td valign="top">

Create



</td>
<td valign="top">

 <code>create using "<i class="varname">&lt;custom exit&gt;</i>"</code> 



</td>
<td valign="top">

The xsodata library calls the exit *<custom exit\>* instead of creating the entity directly



</td>
</tr>
<tr>
<td valign="top">

Update



</td>
<td valign="top">

 <code>update using "<i class="varname">&lt;custom exit&gt;</i>"</code> 



</td>
<td valign="top">

The xsodata library calls the exit *<custom exit\>* instead of updating the entity directly



</td>
</tr>
<tr>
<td valign="top">

Delete



</td>
<td valign="top">

 <code>delete using "<i class="varname">&lt;custom exit&gt;</i>"</code> 



</td>
<td valign="top">

The xsodata library calls the exit *<custom exit\>* instead of deleting the entity directly



</td>
</tr>
</table>

XS Odata also allows you to combine both validation exits and modification exits in the same request, as illustrated in the following example:

> ### Sample Code:  
> ```
> create using "<custom exit>" events(before "<custom exit 1>", after "<custom exit 2>", ...) 
> ```



<a name="loio03735142bfd647c2a016fcd9359f3348__section_r4t_rp3_5z"/>

## Exit Execution Order for XS OData Requests

For **single** OData requests, the following execution order applies for the custom exit:

**Exit Execution Order for Single OData Requests**


<table>
<tr>
<th valign="top">

Odata Request Element



</th>
<th valign="top">

Action



</th>
<th valign="top">

Exit Execution Order



</th>
</tr>
<tr>
<td valign="top">

Request \#



</td>
<td valign="top">

Process the request



</td>
<td valign="top">

1.  `before`

2.  `using` \(or implicit update happens\)

3.  `after`

4.  `precommit`

5.  Data is committed to the database

6.  `postcommit`




</td>
</tr>
</table>

The following table shows the execution order applied to custom exits for **batch** OData requests:

> ### Note:  
> This example assumes that there are two \(2\) requests and the batch request also includes a change set with 2 requests.

**Exit Execution Order for OData Batch Requests**


<table>
<tr>
<th valign="top">

OData Batch-Request Element



</th>
<th valign="top">

Action



</th>
<th valign="top">

Exit Execution Order



</th>
</tr>
<tr>
<td valign="top">

Request 1



</td>
<td valign="top">

Process the request



</td>
<td valign="top">

Single OData request execution order



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Change set



</td>
<td valign="top">

Process request 1 in the change set



</td>
<td valign="top">

1.  `before`

2.  `using` 

3.  `after`




</td>
</tr>
<tr>
<td valign="top">

Process request 2 in the change set



</td>
<td valign="top">

1.  `before`

2.  `using` 

3.  `after`




</td>
</tr>
<tr>
<td valign="top">

Process the commit operation



</td>
<td valign="top">

1.  `precommit` of the first request

2.  `precommit` of the second request

3.  Commit the requested data

4.  `postcommit` of the first request

5.  `postcommit` of the second request




</td>
</tr>
<tr>
<td valign="top">

Request 2



</td>
<td valign="top">

Process request 2



</td>
<td valign="top">

Single OData request execution order



</td>
</tr>
</table>



<a name="loio03735142bfd647c2a016fcd9359f3348__section_im1_pr3_5z"/>

## Exit Implementation

You can choose to perform the exit in any of the following ways:

-   [JavaScript Function](custom-exits-for-odata-requests-0373514.md#loio03735142bfd647c2a016fcd9359f3348__subsection_rdv_ds3_5z)

-   [Stored procedure](custom-exits-for-odata-requests-0373514.md#loio03735142bfd647c2a016fcd9359f3348__subsection_p2v_ds3_5z)




### XS Odata Custom Exit as an XS JavaScript Function

The JavaScript function needs to be implemented within an XS JavaScript library \(`*.xsjslib` artifact\). There is no need to use the export mechanism of Node.js; a plain function is all you need, as illustrated in the following example:.

> ### Sample Code:  
> ```
> //myLoggingInfrastructure.xsjslib
>  
> function my_create_before_exit(param) { 
> } 
> ```

The input parameter param is an object with the following content:

1.  `connection`

    The SQL connection used in the OData request

2.  `beforeTableName`

    The name of a temporary table with the single entry **before** the operation \(UPDATE and DELETE events only\)

3.  `afterTableName`

    The name of a temporary table with the single entry **after** the operation \(CREATE and UPDATE events only\)


The content of the temporary tables can be fetched using the available SQL connection as illustrated in the following example:

> ### Sample Code:  
> ```
> var stmt = 'select * from "'+ param.afterTableName + '"', 
>     xStmt = param.connection.prepareStatement( stmt ).executeQuery(), 
>     data = xStmt._rows[0]; // {col1:val1, col2:val2, ...} 
> ```

For the custom exit function, there are two possibilities to handle an error:

1.  Throw an error

    Use the function `throw "error message";`.

    > ### Note:  
    > The response has the status code “`500`”, which cannot be modified.

2.  Return an object

    Return an object with the following structure:

    > ### Sample Code:  
    > ```
    > return{ 
    >    HTTP_STATUS_CODE: code, // e.g. 400, 500, etc. 
    >    ERROR_MESSAGE: 'error message', 
    >    DETAILS: 'more details'
    > }; 
    > ```

    > ### Note:  
    > This method enables you to add more details and control the status code of the response.


Within the xsodata files, exit functions are referenced with a colon \(:\) separated string, for example: <code><i class="varname">&lt;directory&gt;</i>:<i class="varname">&lt;file&gt;</i>::<code>function</code></code> .

> ### Sample Code:  
> ```
> sap.abc.xyz:myLoggingInfrastructure.xsjslib::my_create_before_exit
> ```

-   `sap.abc.xyz`

    References a directory

-   `myLoggingInfrastructure.xsjslib`

    References a XS JavaScript library \(`xsjslib` file\)

-   `my_create_before_exit`

    References the exit function


The following example shows an XS JavaScript startup configuration with two root folders `/_SYS_REPO` and `/my_content`:

> ### Sample Code:  
> ```
> //Start xsjs listener 
> xsjs({
>    compress: false, 
>    rootDirs: [ 
>       path.join(__dirname, '_SYS_REPO') 
>       path.join(__dirname, 'my_content') 
>    ], 
>    ...}).listen(...)
> ```

In the example above, the file `myLoggingInfrastructure.xsjslib` must be stored in one of the following locations:

-   <code><i class="varname">&lt;app directory&gt;</i>/_SYS_REPO/sap/abc/xyz/myLoggingInfrastructure.xsjslib</code>

-   <code><i class="varname">&lt;app directory&gt;</i>/my_content/sap/abc/xyz/myLoggingInfrastructure.xsjslib</code>




### XS Odata Custom Exit as an SQLScript Stored Procedure

If you register a custom exit for an OData write request in the form of an SQLScript procedure, the signature of the registered script must follow specific rules, for example, depending on whether it is registered for *entity* or *link* write operations and depending on the operation itself. The signature must also have table-typed parameters for both input and output:

-   Entity Write Operations
-   Link Write Operations

For **entity** write operations, the methods registered for the CREATE operation are passed a table containing the new entry that must be inserted into the target table; the UPDATE operation receives the entity both before and after the modification; the DELETE operation receives the entry that must be deleted. The table type of the parameters \(specified with the *EntityType* keyword in the table below\) corresponds to the types of the exposed entity.

**Entity Write Operations**


<table>
<tr>
<th valign="top">

Script Type



</th>
<th valign="top">

Create



</th>
<th valign="top">

Update



</th>
<th valign="top">

Delete



</th>
</tr>
<tr>
<td valign="top">

before, after, precommit, using



</td>
<td valign="top">

IN new EntityType, OUT error ErrorType



</td>
<td valign="top">

IN new EntityType, IN old EntityType, OUT error ErrorType



</td>
<td valign="top">

IN old EntityType, OUT error ErrorType



</td>
</tr>
<tr>
<td valign="top">

postcommit



</td>
<td valign="top">

IN new EntityType



</td>
<td valign="top">

IN new EntityType, IN old EntityType



</td>
<td valign="top">

IN old EntityType



</td>
</tr>
</table>

For **link** write operations, all exits that are executed before the commit operation take two table-typed input parameters and one table-typed output parameter. The first parameter must correspond to the structure of the entity type at the **principal** end of the association; the second parameter must correspond to the **dependent** entity type.

**Link Write Operations**


<table>
<tr>
<th valign="top">

Script Type



</th>
<th valign="top">

Create, Update, Delete



</th>
</tr>
<tr>
<td valign="top">

before, after, precommit, using



</td>
<td valign="top">

IN principal PrincipalEntityType, IN dependent DependentEntityType, OUT error ErrorType



</td>
</tr>
<tr>
<td valign="top">

postcommit



</td>
<td valign="top">

IN principal PrincipalEntityType, IN dependent DependentEntityType



</td>
</tr>
</table>

> ### Note:  
> Parameter types \(`IN`, `OUT`\) are checked during activation; the data types of table type columns are **not** checked.

The `OUT` parameter enables you to return error information. The first row in the OUT table is then serialized as `inner error` in the error message. If no error occurs, the OUT table must remain empty. The structure of the table type `ErrorType` is not restricted. Any columns with special names `HTTP_STATUS_CODE` and `ERROR_MESSAGE` are mapped to common information in the OData error response. Content of columns with other names are serialized into the `inner error` part of the error message that allows the return of custom error information.

**Error Message Content**


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Type



</th>
<th valign="top">

Value Range



</th>
<th valign="top">

Error Response Information



</th>
</tr>
<tr>
<td valign="top">

HTTP\_STATUS\_CODE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

400-417 \(default: 400\)



</td>
<td valign="top">

The HTTP response status code



</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE



</td>
<td valign="top">

NVARCHAR



</td>
<td valign="top">

 



</td>
<td valign="top">

The error message \(*<message\>*\)



</td>
</tr>
</table>

> ### Note:  
> If the SQLScript procedure throws an exception or writes an error messages to the `OUT` parameter table, the OData write operation is aborted. If more than one error message is added, only the content of the first row is returned in the resulting error message. Any scripts registered for the `postcommit` event must not have an `OUT` parameter as the write operation cannot be aborted at such a late stage, even in the event of an error.

The following example illustrates a typical error-type table type, which is defined in a design-time file that must have the `.hdbtabletype` file suffix, for example `error.hdbtabletype`:

```
"sample.odata::error" AS TABLE (
	"HTTP_STATUS_CODE" INTEGER,
	"ERROR_MESSAGE" NVARCHAR(100),
	"DETAIL"  NVARCHAR(100) 
)

```

The following example shows how information is extracted from the error table if an error occurs during the execution of a create procedure for an OData write operation:

```
create procedure "sample.odata::createmethod"(IN new "sample.odata::table", OUT error "sample.odata::error") 
language sqlscript 
sql security invoker as 
     id INT;
begin
     select ID into id from :new;
     if :id < 1000 then
          error = select 400 as http_status_code, 
          'invalid ID' error_message, 
          'value must be >= 1000' detail from dummy;
     else
          insert into "sample.odata::table" values (:id);
     end if;
end;

```

**Related Information**  


[Tutorial: Creating a Validation Exit with SQLScript](tutorial-creating-a-validation-exit-with-sqlscript-3621f08.md "Use SQLScript to create a custom validation exit which runs server-side verification and data-consistency checks for an OData update operation.")

