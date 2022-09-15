<!-- loio5c253fd9539340369478809b3977be72 -->

# Memory Size Options



<a name="loio5c253fd9539340369478809b3977be72__memory_types"/>

## Memory Types

There are three memory types that can be sized and for each memory type there is a command-line option, which is passed to the JVM.

-   HEAP

    The initial and maximum sizes of the HEAP memory are controlled by the *\-Xms* and *\-Xmx* options respectively.

-   METASPACE

    The initial and maximum sizes of the METASPACE memory are controlled by the *\-XX:MetaspaceSize* and *\-XX:MaxMetaspaceSize* options.

-   STACK

    The size of the STACK is controlled by the *\-Xss* option.




## Changing Memory Settings with the Memory Calculator

The memory calculator uses calculation techniques that allocate the available memory to the memory types. The total available memory is first allocated to each memory type in proportion to its weighting \(this is called ‘balancing'\). If the resultant size of any memory type lies outside its range, the size is constrained to the range, the constrained size is excluded from the remaining memory, and no further calculation is required for that memory type. After that, the remaining memory is balanced against the memory types that are left, and the check is repeated until no calculated memory sizes lie outside their ranges. These iterations terminate when none of the sizes of the remaining memory types are constrained by their corresponding ranges.

The memory calculator uses the following calculation techniques:

-   Memory calculations using absolute memory sizes

-   Memory calculations using relative memory weights




<a name="loio5c253fd9539340369478809b3977be72__custom_values"/>

## Setting Custom Weights, Sizes, and Initials

You can set custom values in the manifest file before the application is staged by using the following parameters:

-   `memory_sizes`

    The data for this parameter specifies the absolute values for the memory properties of the SAP JVM: -Xms, -Xmx, -Xss, -XX:MaxMetaspaceSize, or -XX:MetaspaceSize.

-   `memory_heuristic`s

    The data for this parameter specifies the relative weights for the different memory types.

-   `memory_initials`

    This parameter is used to adjust the initial values for HEAP and METASPACE types.


> ### Sample Code:  
> Setting HEAP memory to 8.5 times larger than the STACK memory.
> 
> ```
>   env:
>     JBP_CONFIG_SAPJVM:  "[memory_calculator: {memory_heuristics: {heap: 85, stack: 10}}]"
> 
> ```

Furthermore, you can change the sizes during the application run time with the `cf set-env` command, as follows:

-   To set custom weights, use the JBP\_CONFIG\_SAPJVM\_MEMORY\_WEIGHTS environment variable.

    > ### Sample Code:  
    > ```
    > xs set-env myapp JBP_CONFIG_SAPJVM_MEMORY_WEIGHTS "heap:5,stack:1,metaspace:3,native:1"
    > ```

-   To set custom sizes, use the JBP\_CONFIG\_SAPJVM\_MEMORY\_SIZES environment variable.

    > ### Sample Code:  
    > ```
    > xs set-env myapp JBP_CONFIG_SAPJVM_MEMORY_SIZES "heap: 30m..400m, stack: 2m.., metaspace: 10m..12m"
    > ```

-   To set custom initials, use the JBP\_CONFIG\_SAPJVM\_MEMORY\_INITIALS environment variable.

    > ### Sample Code:  
    > ```
    > xs set-env myapp JBP_CONFIG_SAPJVM_MEMORY_INITIALS "heap: 50%, metaspace: 50%"
    > ```


> ### Note:  
> If you specify values for weight and size at the same time, the size values take precedence over the weight values.



<a name="loio5c253fd9539340369478809b3977be72__java_options"/>

## Java Options

You can set the Java options by using the following parameters:

-   `from_environment`

    This parameter expects a Boolean value which specifies if the value of the *<JAVA\_OPTS\>* environment variable must be taken into account. By default, it is set to “`false`”.

-   `java_opts`

    This section is used for additional Java options such as `-Xloggc:$PWD/beacon_gc.log -verbose:gc -XX:NewRatio=2`. By default, no additional options are provided.


