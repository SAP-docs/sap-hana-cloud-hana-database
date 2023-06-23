<!-- loiof797a90372ad4bc4acf882c75dc51e33 -->

# Cancel a Running Make Operation in an SAP HDI Container

An HDI container administrator can cancel a `make` operation that is running in an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), an HDI container administrator can cancel a running make in a container `C`, for example, if it is taking longer to complete than expected. This is mainly intended for canceling asynchronous makes \(`C#DI.MAKE_ASYNC`\) but also works for synchronous ones \(`C#DI.MAKE`\). When an asynchronous make is started, it returns a request ID identifying that make process. This request ID can then be used in a call to the `C#DI.CANCEL` procedure for canceling this process.



<a name="loiof797a90372ad4bc4acf882c75dc51e33__steps_phl_b42_l1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the target HDI container \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Cancel the make operation.

    Enter the following SQL code:

    > ### Sample Code:  
    > ```sql
    > CALL C#DI.CANCEL(12345, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

    1.  Adjust the name of the container \(“C”\) in the `CALL` statement to reflect your target container.

    2.  Replace “`12345`” in the `CALL` statement with the request ID of the make process you want to cancel.

        > ### Tip:  
        > The procedure `C#DI.MAKE` returns one or more result sets, which contain the request ID and the return code.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

