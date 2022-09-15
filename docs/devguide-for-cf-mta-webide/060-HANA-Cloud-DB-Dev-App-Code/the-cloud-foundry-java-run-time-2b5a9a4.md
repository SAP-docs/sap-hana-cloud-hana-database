<!-- loio2b5a9a4c33b54a49ba9ce4e30d04f02a -->

# The Cloud Foundry Java Run Time

 SAP Business Technology Platform provides a Cloud Foundry Java run time to which you can deploy your Java applications.

The Java run time for Cloud Foundry on SAP Business Technology Platform provides the Tomcat, TomEE, TomEE 7, and Java Main run times to deploy your Java code. During application deployment, the build pack ensures that the correct SAP Java Virtual Machine \(JVM\) is provided and that the appropriate data sources for the SAP HDI container are bound to the corresponding application container.

> ### Note:  
> The Cloud Foundry run-time platform on SAP Business Technology Platform makes no assumptions about which frameworks and libraries to use to implement the Java micro service.

Cloud Foundry on SAP Business Technology Platform provides the following components to help build a Java micro service:

-   Tomcat, TomEE, TomEE 7, and Java Main run times
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

When you use the Tomcat, TomEE or TomEE 7 run time, you can rely on certain standard APIs:


<table>
<tr>
<th valign="top">

Run time



</th>
<th valign="top">

Tomcat/TomEE



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

TomEE



</td>
<td valign="top">

Apache TomEE JAX-RS \(Java EE 6\)



</td>
<td valign="top">

Java Servlets 3.0

Java ServerPages \(JSP\) 2.2

Expression Language \(EL\) 2.2

Debugging Support for Other Languages 1.0

Standard Tag Library for JavaServer Pages \(JSTL\) 1.2

Java API for WebSocket 1.1

Java ServerFaces \(JSF\) 2.0

Java Transaction API \(JTA\) 1.1

Java Persistence API \(JPA\) 2.0

Java Contexts and Dependency Injection \(CDI\) 1.0

Java Authentication and Authorization Service \(JAAS\)

Java Authorization Contract for Containers \(JACC\) 1.3

JavaMail API 1.4

Bean Validation 1.0

Enterprise JavaBeans 3.1

Java API for RESTful Web Services \(JAX-RS\) 1.1



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

