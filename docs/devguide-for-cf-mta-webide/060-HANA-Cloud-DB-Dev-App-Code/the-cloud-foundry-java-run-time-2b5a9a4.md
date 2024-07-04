<!-- loio2b5a9a4c33b54a49ba9ce4e30d04f02a -->

# The Cloud Foundry Java Run Time

SAP Business Technology Platform provides a Cloud Foundry Java run time to which you can deploy your Java applications.

The Java run time for Cloud Foundry on SAP Business Technology Platform provides the Tomcat, TomEE 7, and Java Main run times to deploy your Java code. During application deployment, the build pack ensures that the correct SAP Java Virtual Machine \(JVM\) is provided and that the appropriate data sources for the SAP HDI container are bound to the corresponding application container.

> ### Note:  
> The Cloud Foundry run-time platform on SAP Business Technology Platform makes no assumptions about which frameworks and libraries to use to implement the Java micro service.

Cloud Foundry on SAP Business Technology Platform provides the following components to help build a Java micro service:

-   Tomcat, TomEE, and Java Main run times

    > ### Note:  
    > The outdated TomEE 1.7 version is no longer included in the SAP Java Buildpack. Although TomEE 1.7 will continue to be supported until the end of the deprecation period, it is recommended to migrate to TomEE 7 as soon as possible, as described in the *TomEE Migration Guide* listed in *Related Information* below. TomEE 7 is already included in previous versions of the SAP Java Buildpack.

-   Setup of SAP HANA data sources
-   Java library to support authentication with JSON Web Tokens \(JWT\)

    Used for communication between the application router, micro services, and the database


To use Tomcat on SAP JVM 8, specify the `java-buildpack` in your multitarget application's deployment manifest \(`manifest.yml`\), as illustrated in the following example:

> ### Sample Code:  
> ```
> applications: 
>   - name: my-java-service 
>     buildpack: path/to/java-buildpack 
>     services: 
>       - my-hdi-container
>       - my-uaa-instance
> 
> ```

When you use the Tomcat or TomEE 7 run time, you can rely on certain standard APIs:


<table>
<tr>
<th valign="top">

Run time

</th>
<th valign="top">

Tomcat

</th>
<th valign="top">

Supported specification version

</th>
</tr>
<tr>
<td valign="top">

Tomcat

</td>
<td valign="top">

Apache Tomcat 8

</td>
<td valign="top">

Java Servlets 3.1

Java ServerPages \(JSP\) 2.3

Expression Language \(EL\) 3.0

Debugging Support for Other Languages 1.0

Java API for WebSocket 1.1

</td>
</tr>
<tr>
<td valign="top">

TomEE 7

</td>
<td valign="top">

Apache TomEE 7 \(Java EE 7 Web Profile\)

</td>
<td valign="top">

Java Servlet 3.1

JavaServer Pages \(JSP\) 2.3

Expression Language \(EL\) 3.0

WebSocket 1.1

Standard Tag Library for JavaServer Pages \(JSTL\) 1.2

Java API for RESTful Web Services \(JAX-RS\) 2.0

JavaServer Faces \(JSF\) 2.2

Debugging Support for Other Languages 1.0

Enterprise JavaBeans \(EJB\) Lite 3.2

Java Transaction API \(JTA\) 1.2

Java Persistence API \(JPA\) 2.1

Bean Validation 1.1

Managed Beans 1.0

Interceptors 1.2

Common Annotations for Java Platform 1.2

Dependency Injection for Java 1.0

Contexts and Dependency Injection for Java EE platform 1.1

</td>
</tr>
</table>

**Related Information**  


[TomEE Migration Guide](http://help.sap.com/disclaimer?site=https://tomee.apache.org/developer/migration/tomee-1-to-7.html)

