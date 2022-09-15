<!-- loio5176fc47760c4c6f89612af5551715f2 -->

# Change Application Settings for the Cloud Foundry Java Run Time

You can change the run-time settings in your Java application's manifest file.

 <a name="task_fjt_m4x_k1b"/>

<!-- task\_fjt\_m4x\_k1b -->

## Set the Java Virtual Machine \(JVM\)



<a name="task_fjt_m4x_k1b__context_kqz_wpx_k1b"/>

## Context

You can specify the Java Virtual Machine \(JVM\) that your application needs by setting the *<JBP\_CONFIG\_COMPONENTS\>* environment variable in the application’s `manifest.yml` file before pushing the application to the run-time environment. The following list shows which JVMs the run-time platform currently supports and indicates the corresponding environment variable to use in the configuration:

-   SAP JRE:

    `com.sap.xs.java.buildpack.jre.SAPJVM`

-   SAP JDK:

    `com.sap.xs.java.buildpack.jdk.SAPJVMJDK`

-   SAPMachine JDK:

    `com.sap.xs.java.buildpack.jdk.SAPMachineJDK`


For example, if your application requires the SAP JDK, use the following configuration in the application's `manifest.yml` file:

```
env
  JBP_CONFIG_COMPONENTS: [jres: ['com.sap.xs.java.buildpack.jdk.SAPJVMJDK']]
```

If the *<JBP\_CONFIG\_COMPONENTS\>* environment variable is not set, the default JVM for a Java application is the JRE.

> ### Note:  
> The `SapMachine` run time is supported only for Tomcat and Java Main application containers.

 <a name="task_ynm_3sy_lv"/>

<!-- task\_ynm\_3sy\_lv -->

## Set the TomEE or TomEE 7 Run Time



## Context

The default Java run-time environment is “Tomcat”. However, you can change the desired Java run-time environment to “TomEE” or “TomEE 7” by setting the *<TARGET\_RUNTIME\>* environment variable in the Java application's `manifest.yml`, as illustrated in the following examples:

> ### Code Syntax:  
> For TomEE
> 
> ```
> env:
>     TARGET_RUNTIME: tomee
> 
> ```

> ### Code Syntax:  
> For TomEE 7
> 
> ```
> env:
>     TARGET_RUNTIME: tomee7
> 
> ```

 <a name="task_nwz_fhw_3v"/>

<!-- task\_nwz\_fhw\_3v -->

## Configure Memory Sizes



## Context

The HEAP, METASPACE and STACK memory types are configured with a corresponding default size. However, the default values can also be customized, as illustrated in the following example.



<a name="task_nwz_fhw_3v__steps-unordered_fbz_t1z_lv"/>

## Procedure

-   Configure the memory sizes during the staging phase.

    If this is the first staging of the application \(the application has not been pushed to Cloud Foundry\), provide *<JBP\_CONFIG\_SAPJVM\>* environment variable in the `manifest.yml` file of the application and then stage the application.

    > ### Example:  
    > Sample `manifest.yml`
    > 
    > ```
    > ---
    > applications:
    > - name: <app-name>
    >   memory: 512M
    > ...
    >   env:
    >     JBP_CONFIG_SAPJVM:  "[memory_calculator: {memory_heuristics: {heap: 85, stack: 10}}]"
    > 
    > ```

    For more information about memory types for the Cloud Foundry Java run-time environment, see *Memory Size Options* in *Related Information*.

-   Configure the memory sizes during the application run time.

    This configuration can be changed multiple times after the application is staged and does not require re-staging.

    1.  Open the command prompt.

    2.  Set custom weights, sizes, and initials.

        For more information, see *Memory Size Options* in *Related Links*.

    3.  Restart the application.



 <a name="task_vq2_tlw_3v"/>

<!-- task\_vq2\_tlw\_3v -->

## Configure Other Memory Options



## Context

You can add custom JVM properties as this configuration is done once and can be changed only when the application is re-staged.

For more information about the Java run-time options, see *Related Links*.



<a name="task_vq2_tlw_3v__steps-unordered_tzj_ftf_mv"/>

## Procedure

-   Use an environment variable in the manifest file.

    If this is the first staging of the application \(the application has not yet been “pushed” to Cloud Foundry\), provide *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable in the `manifest.yml` file of the application and then stage the application.

    > ### Sample Code:  
    > Excerpt from a Java `manifest.yml` file
    > 
    > ```
    > ---
    > applications:
    > - name: <app-name>
    >   memory: 512M
    > ...
    >   env:
    >     JBP_CONFIG_JAVA_OPTS: '[from_environment: false, java_opts: ''-DtestJBPConfig=^%PATH^% -DtestJBPConfig1="test test" -DtestJBPConfig2="%PATH%"'']'
    > ```

    > ### Note:  
    > A single quote is used to enclose the *<JBP\_CONFIG\_JAVA\_OPTS\>* string in the YML file because the string can contain any one \(or combination\) of the following characters: *:*, *\{*, *\}*, *\[*, *\]*, *,*, *&*, *\**, *\#*, *?*, *|*, *\-*, *<*, *\>*, *=*, *!*, *%*, *@*, *\\*.

-   Set the environment variable with a the `cf set-env` command.

    If the application is already available in Cloud Foundry, and the application developer wants to fine-tune the JVM additionally with an additional or modified property, a new value for the *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable can be specified with the `cf set-env` command. The new values will overwrite the default \(or set\) values in the corresponding build pack the next time the application is staged.

    > ### Example:  
    > ```
    > cf set-env myapp JBP_CONFIG_JAVA_OPTS "[from_environment: false, java_opts: '-DtestJBPConfig=^%PATH^% -DtestJBPConfig1=\"test test\" -DtestJBPConfig2=\"^%PATH^%\"']"
    > ```

    > ### Note:  
    > When the Java options are specified on the command line with the `cf set-env` command, the string defining the new values must be enclosed in double quotes, for example, <code>“<i class="varname">&lt;New-config_values&gt;</i>”</code>.


**Related Information**  


[Memory Size Options](memory-size-options-5c253fd.md)

[Java Memory Options](memory-size-options-5c253fd.md#loio5c253fd9539340369478809b3977be72__java_options)

