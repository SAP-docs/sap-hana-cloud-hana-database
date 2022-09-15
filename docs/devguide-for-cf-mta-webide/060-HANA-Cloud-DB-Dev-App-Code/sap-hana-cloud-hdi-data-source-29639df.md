<!-- loio29639df57e984a0e80aec048d1a0fe13 -->

# SAP HANA Cloud HDI Data Source

Set up HDI data sources for multitarget Java applications in SAP HANA Cloud.



To use a SAP HANA Cloud HDI container from your Java run time, you must create a service instance for the HDI container and bind the service instance to the Java application. To create a service instance, use the `cf create-service` command, as illustrated in the following example:

> ### Sample Code:  
> ```
> cf create-service hana hdi-shared my-hdi-container
> ```

To bind the service instance to a Java application, specify the service instance in the Java application's deployment manifest file \(`manifest.yml`\).

> ### Sample Code:  
> ```
> services: 
>    - my-hdi-container
> ```

Next, add the resource reference to the `web.xml` file, which must have the name of the service instance:

> ### Sample Code:  
> ```
> <resource-ref>
>   <res-ref-name>jdbc/my-hdi-container</res-ref-name>
>   <res-type>javax.sql.DataSource</res-type>
> </resource-ref>
> ```

Look up the data source in your code; you can find the reference to the data source in the following ways:

-   Annotations

    ```
    @Resource(name = "jdbc/my-hdi-container")
    private DataSource ds;
    ```

-   Java Naming and Directory Interface \(JNDI\) look-up

    ```
    Context ctx = new InitialContext(); 
    return (DataSource) ctx.lookup("java:comp/env/jdbc/my-hdi-container");
    ```


