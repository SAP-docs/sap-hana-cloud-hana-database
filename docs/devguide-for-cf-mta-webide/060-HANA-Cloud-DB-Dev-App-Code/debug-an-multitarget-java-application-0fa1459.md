<!-- loio0fa1459affac4af5ab12f86de4814b9a -->

# Debug an Multitarget Java Application

Debug a multitarget Java application in Cloud Foundry.



<a name="loio0fa1459affac4af5ab12f86de4814b9a__prereq_p5j_jy1_hlb"/>

## Prerequisites

You can use this procedure only if you can restart your Java application or the application has not yet been pushed.



## Procedure

1.  Add an environment variable to the Java application's manifest file \(`manifest.yml`\).

    Open the `manifest.yml` file and add the *<JBP\_CONFIG\_JAVA\_OPTS\>* variable, as illustrated in the following example:

    > ### Example:  
    > ```
    > 
    > ---
    > applications:
    > - name: test-java
    >   memory: 256M
    >   instances: 1
    >   path: target/test-java.war
    >   env:
    >     TARGET_RUNTIME: tomcat
    >     JBP_CONFIG_JAVA_OPTS: [java_opts: '-agentlib:jdwp=transport=dt_socket,address=8000,server=y,suspend=y']
    > 
    > ```

    > ### Note:  
    > With *<JBP\_CONFIG\_JAVA\_OPTS\>*, you set options to the JVM, which will activate the Java Debug Wire Protocol \(JDWP\) agent. You could change the desired options to your liking. For more information, about the available options, see *\-agentlib:jdwp and -Xrunjdwp sub-options* in *Related Information* below.

2.  Push the application.

    To push the application to the Java run-time, use the following command:

    `cf push -f manifest.yml`

    Before the application starts, it waits for a debugger to connect to port 8000.

3.  Attach the debugger to the specified port.

    > ### Caution:  
    > Your application will fail to start if you do not attach a debugger in time.


**Related Information**  


[\-agentlib:jdwp and -Xrunjdwp sub-options \(Java SE documentation\)](http://docs.oracle.com/javase/7/docs/technotes/guides/jpda/conninv.html#jdwpoptions)

