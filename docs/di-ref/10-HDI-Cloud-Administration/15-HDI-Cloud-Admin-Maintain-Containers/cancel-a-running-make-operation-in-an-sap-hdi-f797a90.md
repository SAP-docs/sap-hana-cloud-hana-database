<!-- loiof797a90372ad4bc4acf882c75dc51e33 -->

# Cancel a Running Make Operation in an SAP HDI Container

An HDI container administrator can cancel a `make` operation that is running in an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), an HDI container administrator can cancel a running make in a container *<container\_name\>*, for example, if it is taking longer to complete than expected. This is mainly intended for canceling asynchronous makes \(<code><i class="varname">&lt;container_name&gt;</i>#DI.MAKE_ASYNC</code>\) but also works for synchronous ones \(<code><i class="varname">&lt;container_name&gt;</i>#DI.MAKE</code>\). When an asynchronous make is started, it returns a request ID identifying that make process. This request ID can then be used in a call to the <code><i class="varname">&lt;container_name&gt;</i>#DI.CANCEL</code> procedure for canceling this process.



<a name="loiof797a90372ad4bc4acf882c75dc51e33__steps_phl_b42_l1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the target HDI container \(for example, *<container\_name\>*\).

2.  Open the SQL editor for this database.

3.  Cancel the make operation.

    Enter the following SQL code:

    > ### Sample Code:  
    > ```sql
    > CALL <container_name>#DI.CANCEL(12345, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

    1.  Replace *<container\_name\>* in the `CALL` statement with the name of your target container.

    2.  Replace “`12345`” in the `CALL` statement with the request ID of the make process you want to cancel.

        > ### Tip:  
        > The procedure <code><i class="varname">&lt;container_name&gt;</i>#DI.MAKE</code> returns one or more result sets, which contain the request ID and the return code.


4.  Run the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

