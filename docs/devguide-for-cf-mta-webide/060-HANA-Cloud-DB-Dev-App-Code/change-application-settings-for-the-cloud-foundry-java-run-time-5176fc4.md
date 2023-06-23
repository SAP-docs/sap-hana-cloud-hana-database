<!-- loio5176fc47760c4c6f89612af5551715f2 -->

# Change Application Settings for the Cloud Foundry Java Run Time

You can change the run-time settings in your Java application's manifest file.

 <a name="task_fjt_m4x_k1b"/>

<!-- task\_fjt\_m4x\_k1b -->

## Set the Java Virtual Machine \(JVM\)



<a name="task_fjt_m4x_k1b__context_kqz_wpx_k1b"/>

## Context

You can specify the Java Virtual Machine \(JVM\) that your application needs by setting the *<JBP\_CONFIG\_COMPONENTS\>* environment variable in the application’s `manifest.yml` file before pushing the application to the run-time environment. Depending on the Java version your application requires, choose one of the options described in the following sections.



### Using Java 8 with the SAP JVM JRE

If your application uses Java 8 \(provided by the SAP JVM\) and a JRE is sufficient, use the following configuration in the application's `manifest.yml` file:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: '{ "jres": ["com.sap.xs.java.buildpack.jre.SAPJVM"] }'
  ...
```

If the *<JBP\_CONFIG\_COMPONENTS\>* environment variable is not set, the default JVM for the Java application is the JRE.



### Using Java 8 with the SAP JVM JDK

If your application uses Java 8 \(provided by the SAP JVM\) and requires a JDK, use the following configuration in the application's `manifest.yml` file:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: '{ "jres": ["com.sap.xs.java.buildpack.jdk.SAPJVMJDK"] }'
  ...
```



### Using Java 11 or Java 17 with the SapMachine JRE

If your application uses Java 11 or Java 17 provided by the SapMachine, and a JRE is sufficient, use the following configuration in the application's `manifest.yml` file:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: '{ "jres": ["com.sap.xs.java.buildpack.jre.SAPMachineJRE"] }'
    JBP_CONFIG_SAP_MACHINE_JRE: '{ "version": "17.+" }'
  ...
```

Use the environment variable *<JBP\_CONFIG\_SAP\_MACHINE\_JRE\>* to configure the Java version. You can specify a strict version or use the '+' wildcard to define a major Java version in general, as shown in the example above. If you do not specify this property, the default is Java 11.



### Using Java 11 or Java 17 with the SapMachine JDK

If your application uses Java 11 or Java 17 provided by the SapMachine and requires a JDK, use the following configuration in the application's `manifest.yml` file:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: '{ "jres": ["com.sap.xs.java.buildpack.jdk.SAPMachineJDK"] }'
    JBP_CONFIG_SAP_MACHINE_JDK: '{ "version": "17.+" }'
  ...
```

Use the environment variable *<JBP\_CONFIG\_SAP\_MACHINE\_JDK\>* to configure the Java version. You can specify a strict version or use the '+' wildcard to define a major Java version in general, as shown in the example above. If you do not specify this property, the default is Java 11.

 <a name="task_ynm_3sy_lv"/>

<!-- task\_ynm\_3sy\_lv -->

## Set the TomEE 7 Run Time



## Context

The default Java run-time environment is “Tomcat”. However, you can change the desired Java run-time environment to “TomEE 7” by setting the *<TARGET\_RUNTIME\>* environment variable in the Java application's `manifest.yml`, as illustrated in the following examples:

> ### Note:  
> The outdated TomEE 1.7 version is no longer included in the SAP Java Buildpack. Although TomEE 1.7 will continue to be supported until the end of the deprecation period, it is recommended to migrate to TomEE 7 as soon as possible, as described in the *TomEE Migration Guide* listed in *Related Information* below. TomEE 7 is already included in previous versions of the SAP Java Buildpack.

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

    Provide the *<JBP\_CONFIG\_SAPJVM\>* \(or *<JBP\_CONFIG\_SAP\_MACHINE\_\[JRE|JDK\]\>* if you use SapMachine\) environment variable in the `manifest.yml` file of the application and then stage the application.

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
    >     JBP_CONFIG_SAPJVM: '{ "memory_calculator": { "memory_heuristics": { "heap": 85, "stack": 10 } } }'
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

## Configure Custom JVM Properties



## Context

You can add custom JVM properties as this configuration is done once and can be changed only when the application is re-staged.

For more information about the Java run-time options, see *Related Links*.



<a name="task_vq2_tlw_3v__steps-unordered_tzj_ftf_mv"/>

## Procedure

-   Use an environment variable in the manifest file.

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
    >     JBP_CONFIG_JAVA_OPTS: '{ "java_opts": "-Dlog4j2.debug=\"true\" -DcustomProperty=\"<custom_value>\"" }'
    > ```

    > ### Note:  
    > A single quote is used to enclose the *<JBP\_CONFIG\_JAVA\_OPTS\>* string in the YML file because the string can contain any one \(or combination\) of the following characters: *:*, *\{*, *\}*, *\[*, *\]*, *,*, *&*, *\**, *\#*, *?*, *|*, *\-*, *<*, *\>*, *=*, *!*, *%*, *@*, *\\*.

-   Set the environment variable with a the `cf set-env` command.

    If the application is already available in Cloud Foundry, and the application developer wants to fine-tune the JVM additionally with an additional or modified property, a new value for the *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable can be specified with the `cf set-env` command. The new values will overwrite the default \(or set\) values in the corresponding build pack the next time the application is staged.

    > ### Example:  
    > ```
    > cf set-env myapp JBP_CONFIG_JAVA_OPTS '{ "java_opts": "-Dlog4j2.debug=\"true\" -DcustomProperty=\"<custom_value>\"" }'
    > ```

    > ### Note:  
    > When the Java options are specified on the command line with the `cf set-env` command, the string defining the new values must be enclosed in double quotes, for example, <code>“<i class="varname">&lt;New-config_values&gt;</i>”</code>.


 <a name="task_sbr_gp5_plb"/>

<!-- task\_sbr\_gp5\_plb -->

## Using an Agent



<a name="task_sbr_gp5_plb__context_zyr_jp5_plb"/>

## Context

You can use any agent with the SAP Java Build pack. The agent must be included in the `.jar` or `.war` archive of your application. The SAP Java Build pack extracts the agent when the application is deployed.



<a name="task_sbr_gp5_plb__steps-unordered_fgn_qp5_plb"/>

## Procedure

-   To use a Java agent with the SAP Java Build pack, set the *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable using the *\-javaagent* option as shown in the following example:

    ```
    env:
        JBP_CONFIG_JAVA_OPTS: '{ "java_opts": "-javaagent:<PathToYourAgent>" }'
    ```

    > ### Note:  
    > The Java agent is platform-agnostic, but must be compatible to the version of the JVM you are using.

-   You can also use a native agent. Since a native agent is a dynamic library, it must be compatible with the architecture of the platform. For Cloud Foundry, this is Linux x86\_64. As the application developer you must make sure that the correct agent is used and apply updates whenever they are needed. To use a native agent, set the *<JBP\_CONFIG\_JAVA\_OPTS\>* using the *\-agentpath* option as shown in the following example:

    ```
     env:
        JBP_CONFIG_JAVA_OPTS: '{ "java_opts": "-agentpath:<PathToYourAgent>" }'
    ```


 <a name="task_sp5_4sb_3vb"/>

<!-- task\_sp5\_4sb\_3vb -->

## Examples



<a name="task_sp5_4sb_3vb__context_yys_rsb_3vb"/>

## Context

The following example shows how to configure Java 17 with SapMachine JRE, and custom memory calculator and JVM options:

```
---
applications:
- name: <app-name>
  memory: 512M
...
  env:
    JBP_CONFIG_COMPONENTS: '{ "jres": ["com.sap.xs.java.buildpack.jre.SAPMachineJRE"] }'
    JBP_CONFIG_SAP_MACHINE_JRE: '{ "version": "17.+", "memory_calculator": { "memory_heuristics": { "heap": 85, "stack": 10 } } }'
    JBP_CONFIG_JAVA_OPTS: '{ "java_opts": "-Dlog4j2.debug=\"true\" -DcustomProperty=\"<custom_value>\" -javaagent:<PathToYourAgent>" }'
```

**Related Information**  


[Memory Size Options](memory-size-options-5c253fd.md)

[Java Memory Options](memory-size-options-5c253fd.md#loio5c253fd9539340369478809b3977be72__java_options)

[TomEE Migration Guide](http://help.sap.com/disclaimer?site=https://tomee.apache.org/developer/migration/tomee-1-to-7.html)

