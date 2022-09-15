<!-- loio3621f082a10241759f0ec01f56319ae3 -->

# Tutorial: Creating a Validation Exit with SQLScript

Use SQLScript to create a custom validation exit which runs server-side verification and data-consistency checks for an OData **update** operation.



## Prerequisites

To perform this task, you need the following objects:

-   A table to expose, for example, `sample.odata::table.hdbtable`
-   An error type, for example, `sample.odata::error.hdbtabletype`



## Context

In this tutorial, you see how to register an SQL script for an OData update operation; the script verifies, before the execution of the update operation, that the updated value is larger than the previous one. In the example shown in this tutorial, you define the table to be updated and a table type for the error output parameter of the exit procedure.



## Procedure

1.  Create a table definition file using `.hdbtable` syntax.

    The table to expose is defined in `sample.odata:table.hdbtable`, which should look like the following example:

    ```
    COLUMN TABLE "table" (
    	"ID" INTEGER NOT NULL,
    	PRIMARY KEY ("ID")
    );
    
    ```

2.  Create a table type for the error output parameter of the exit procedure.

    The error type file `sample.odata:error.hdbtabletype` should look like the following example:

    ```
    "sample.odata::error" AS TABLE (
    	"HTTP_STATUS_CODE" INTEGER,
    	"ERROR_MESSAGE" NVARCHAR(100),
    	"DETAIL"  NVARCHAR(100) 
    )
    
    ```

3.  Create a procedure that runs before the UPDATE event.

    The procedure script for the `before UPDATE` event must have two table input parameters and one output parameter, for example:

    -   `IN new "sample.odata::table"`
    -   `IN old "sample.odata::table"`
    -   `OUT error "sample.data::error"`

    The procedure `sample.odata:beforeupdate.hdbprocedure` would look like the following example:

    ```
    procedure "sample.odata::beforeupdate"
         (IN new "sample.odata::table", IN old "sample.odata::table", OUT error "sample.odata::error") 
    language sqlscript 
    sql security invoker as 
         idnew INT;
         idold INT;
    begin
         select ID into idnew from :new;
         select ID into idold from :old;
    if :idnew <= :idold then
    error = select 400 as http_status_code, 
         'invalid ID' error_message, 
         'the new value must be larger than the previous' detail from dummy;
    end if;
    end;
    
    ```

4.  Register the procedure to be executed at the `before` event.

    You use the `update events (before “...”)` keywords to register the procedure, as illustrated in the following example of an OData service file:

    ```
    service {
         “sample.odata::table” 
              update events (before “sample.odata::beforeupdate”);
    }
    
    ```


