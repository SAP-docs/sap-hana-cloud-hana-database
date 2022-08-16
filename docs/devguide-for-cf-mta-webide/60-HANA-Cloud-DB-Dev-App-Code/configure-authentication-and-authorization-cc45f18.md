<!-- loiocc45f1833e364d348b5057a60d0b8aed -->

# Configure Authentication and Authorization

You configure authentication and authorization by using the integrated container authentication provided with the Java build pack or the Spring security library.



## Prerequisites

-   You have secured your Cloud Foundry run time.

    To configure authorizations for Java run time, you just need to set them for Cloud Foundry. For more information, see *Setting up Security Artifacts* in *Related Information* below.

    > ### Note:  
    > A role collection must have already been assigned to the user in SAP HANA Cloud. For more information, see the *SAP HANA Cloud Administrators Guide*.

-   You have secured the application router.

    For more information, see *Configure the Multitarget Application Router* in *Related Information* below.

-   You have created an instance of the XS User Account and Authentication \(XSUAA\) service.

    You must have created the `xsuaa` service instance and have bound it to the application for which you want to configure authentication. For more information about creating a service instance, see *Create an Instance of the xsuaa Service* and *Bind the xsuaa Service Instance to the Multitarget Application* in *Related Information*.




## Context

It is possible to enable offline validation of the JSON Web Token \(JWT\) used for authentication purposes; it does not require an additional call to the User Account and Authentication \(UAA\) service. The trust for this offline validation is created by binding the `xsuaa` service instance to your application.

 <a name="task_gnr_wkm_mv"/>

<!-- task\_gnr\_wkm\_mv -->

## Configure Integrated Container Authentication of the SAP Java Buildpack



## Context

The Java build pack includes an authentication method called `XSUAA`. This makes an offline validation of the received JWT token possible. The signature is validated using the verification key received from the service binding to the `xsuaa` service.

To enforce a check for the `$XSAPPNAME.Display` scope, proceed as follows:



<a name="task_gnr_wkm_mv__steps_xjh_hsm_mv"/>

## Procedure

1.  Configure the use of the `XSUAA` authentication method.

    This is done in the `login-config` section of the `web.xml` file.

    Sample `web.xml` file:

    ```
    <?xml version=“1.0” encoding=“UTF-8”?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance
        xmlns="http://java.sun.com/xml/ns/javaee
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
                            http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd
        version=“3.0”>
        <display-name>sample</display-name>
        <login-config>
            <auth-method>XSUAA</auth-method>
        </login-config>
    </web-app>
    
    ```

2.  Add a security constraint to a servlet.

    ```
    import java.io.IOException;
    import javax.servlet.ServletException;
    import javax.servlet.annotation.*;
    import javax.servlet.http.*;
    /**
     * Servlet implementation class HomeServlet
     */
    @WebServlet(“/*”)
    @ServletSecurity(@HttpConstraint(rolesAllowed = { “Display” }))
    public class HomeServlet extends HttpServlet {
        /**
         * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
         */
        protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            response.getWriter().println(“principal” + request.getUserPrincipal());
        }
    
    ```


 <a name="task_w4n_mxp_4mb"/>

<!-- task\_w4n\_mxp\_4mb -->

## Configure Spring Security for Web Applications



<a name="task_w4n_mxp_4mb__context_jhj_fyp_4mb"/>

## Context

Applications using the deprecated Spring Security OAuth can use the Cloud `java-security` client library with the Spring Security Adapter. SAP HANA XS advanced model provides a module for offline validation of the received JSON Web Token \(JWT\). The signature is validated using the verification key received from the XS UAA service. To configure Spring security for your Java Web application, perform the following steps:



<a name="task_w4n_mxp_4mb__steps_om4_g2q_4mb"/>

## Procedure

1.  Specify the relevant libraries in your build manifest.

    Sample `pom.xml`

    ```
    <!-- take the latest version of security dependencies --> 
    <dependency>
         <groupId>org.springframework.security.oauth</groupId>
         <artifactId>spring-security-oauth2</artifactId> 
    </dependency>
    <dependency> 
         <groupId>com.sap.cloud.security.xsuaa</groupId> 
         <artifactId>api</artifactId> 
         <version>2.7.5</version> 
    </dependency> 
    <dependency> 
         <groupId>com.sap.cloud.security</groupId> 
         <artifactId>java-security</artifactId> 
         <version>2.7.5</version> 
    </dependency> 
    ```

2.  Specify the required listeners in your `web.xml`.

    Sample `web.xml`

    ```
    <listener>
      <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener> 
    <context-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>/WEB-INF/spring-security.xml</param-value>
    </context-param> 
    <filter>
      <filter-name>springSecurityFilterChain</filter-name>
      <filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
    </filter> 
    <filter-mapping>
      <filter-name>springSecurityFilterChain</filter-name>
      <url-pattern>/*</url-pattern> 
    </filter-mapping>
    
    ```

3.  Configure the Spring beans by adding `spring-security.xml`.

    Sample `spring-security.xml`

    ```
    <?xml version="1.0" encoding="UTF-8" ?> 
    <beans xmlns="http://www.springframework.org/schema/beans" 
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
     xmlns:oauth="http://www.springframework.org/schema/security/oauth2" 
     xmlns:sec="http://www.springframework.org/schema/security" 
    
     xsi:schemaLocation="http://www.springframework.org/schema/security/oauth2 
       https://www.springframework.org/schema/security/spring-security-oauth2.xsd 
       http://www.springframework.org/schema/security 
       https://www.springframework.org/schema/security/spring-security.xsd 
       http://www.springframework.org/schema/beans 
       https://www.springframework.org/schema/beans/spring-beans.xsd"> 
    
       <!-- protect secure resource endpoints ================================================ -->
       <sec:http pattern="/**" create-session="never" entry-point-ref="oauthAuthenticationEntryPoint" access-decision-manager-ref="accessDecisionManager" authentication-manager-ref="authenticationManager" use-expressions="true">
          <sec:anonymous enabled="false" />
          <sec:intercept-url pattern="/rest/addressbook/deletedata" access="#oauth2.hasScope('Delete')" method="POST" />
          <sec:intercept-url pattern="/**" access="isAuthenticated()" method="GET" />
          <sec:custom-filter ref="resourceServerFilter" before="PRE_AUTH_FILTER" />
          <sec:access-denied-handler ref="oauthAccessDeniedHandler" />
       </sec:http>
       <bean id="oauthAuthenticationEntryPoint" class="org.springframework.security.oauth2.provider.error.OAuth2AuthenticationEntryPoint" />
       <bean id="oauthWebExpressionHandler" class="org.springframework.security.oauth2.provider.expression.OAuth2WebSecurityExpressionHandler" />
       <bean id="accessDecisionManager" class="org.springframework.security.access.vote.UnanimousBased">
          <constructor-arg>
             <list>
                <bean class="org.springframework.security.web.access.expression.WebExpressionVoter">
                   <property name="expressionHandler" ref="oauthWebExpressionHandler" />
                </bean>
                <bean class="org.springframework.security.access.vote.AuthenticatedVoter" />
             </list>
          </constructor-arg>
       </bean>
       <sec:authentication-manager alias="authenticationManager" />
       <oauth:resource-server id="resourceServerFilter" resource-id="springsec" token-services-ref="offlineTokenServices" />
       <bean id="offlineTokenServices" class="com.sap.cloud.security.adapter.spring.SAPOfflineTokenServicesCloud">
         <property name="localScopeAsAuthorities" value="true" />
       </bean>
       <bean id="oauthAccessDeniedHandler" class="org.springframework.security.oauth2.provider.error.OAuth2AccessDeniedHandler" />
       <!-- define properties file =========================================================== -->
       <bean class="com.sap.xs2.security.commons.SAPPropertyPlaceholderConfigurer">
          <property name="location" value="classpath:/application.properties" />
       </bean>
    </beans>
    
    ```

    The contents of this file specify which parts of the micro service are to be made secure. For example, an `HTTP POST` request to `/rest/addressbook/deletedata` requires the `Delete` scope.

4.  Configure the security properties of the service instance in `application.properties`.

    Sample `application.properties` file of a Java application

    ```
    xs.appname=java-hello-world 
    
    ```

5.  Update your Java code.

    The following code snippet shows that not only the requests are authenticated but also that the user principal is available.

    ```
    AccessToken token = SecurityContext.getAccessToken(); 
    String userName = token.getClaimAsString(TokenClaims.USER_NAME); 
    String email = token.getClaimAsString(TokenClaims.EMAIL); 
    boolean hasDeleteScope = token.hasLocalScope("Delete"); 
    ```

6.  Optional: Use the `XSUserInfo` interface.

    You can use the `XSUserInfoAdapter` from `java-security` to access the token data by means of the `XSUserInfo` interface, as illustrated in the following code example:

    ```
    AccessToken token = SecurityContext.getAccessToken(); 
    XSUserInfo userInfo = new XSUserInfoAdapter(token); 
    String hdbToken = userInfo.getHdbToken(); 
    
    ```

    > ### Tip:  
    > For information about using `java-security` to set up basic token validation in plain Java, for example, in cases where applications are not running in a Web context but still need to perform authentication and authorization checks with JWT tokens, see *Configure Authentication and Authorization Checks for Java applications* below.
    > 
    > Note that the token interface used in `java-security` is not compatible with the `XSUserInfo` interface. If you want to use `XSUserInfo`-specific methods such as `getHdbToken`, use the `XSUserInfoAdapter`.


 <a name="task_q5g_11q_4mb"/>

<!-- task\_q5g\_11q\_4mb -->

## Configure Spring Security for Spring Boot Applications



<a name="task_q5g_11q_4mb__context_zsn_l1q_4mb"/>

## Context

Spring Boot Applications can use the Cloud `spring-xsuaa` client library, which provides a module for offline token validation of the received JSON Web Token \(JWT\). The signature is validated using the token keys received from the `XS UAA` service. To configure Spring security for your Spring Boot application, perform the following steps:



<a name="task_q5g_11q_4mb__steps_p33_v1q_4mb"/>

## Procedure

1.  Include the `spring-xsuaa` library.

    The library is available on the Maven Central Repository.

    ```
    <groupId>com.sap.cloud.security.xsuaa</groupId>
    <artifactId>spring-xsuaa</artifactId>
    ```

2.  Read the instructions in the source documentation.

    For more information, see [https://github.com/SAP/cloud-security-xsuaa-integration](https://github.com/SAP/cloud-security-xsuaa-integration) on GitHub.

3.  Authenticate requests with JSON Web tokens \(JWT\).

    For instructions and examples showing how to authenticate requests with JWTs, see the following sample application:

    [Sample application for Spring security](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/samples/spring-security-xsuaa-usage)


 <a name="task_um5_zbq_4mb"/>

<!-- task\_um5\_zbq\_4mb -->

## Configure Authentication and Authorization Checks for Java applications



<a name="task_um5_zbq_4mb__context_pp5_ccq_4mb"/>

## Context

Native Java Applications can use the Cloud `java-security` library to perform basic offline token validation in plain Java. This can be useful for applications that are not running in a Web context but still need to perform authentication and authorization checks using JWT tokens.



<a name="task_um5_zbq_4mb__steps_jd5_ncq_4mb"/>

## Procedure

1.  Include the `java-security` library.

    The library is available on the Maven Central Repository.

    ```
    <groupId>com.sap.cloud.security.xsuaa</groupId>
    <artifactId>java-security</artifactId>
    ```

2.  Read the instructions in the source documentation.

    For more information, see [https://github.com/SAP/cloud-security-xsuaa-integration](https://github.com/SAP/cloud-security-xsuaa-integration) on GitHub.

3.  Authenticate requests with JSON Web tokens \(JWT\).

    For instructions and examples showing how to authenticate requests with JWTs, see the following sample application:

    [Sample application for Java security](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/samples/java-security-usage)


**Related Information**  


[Set up Application Security](../100-HANA-Cloud-DB-Dev-Security/set-up-application-security-b823639.md "Help ensure a multitarget application is protected from Web-based attacks.")

[Configure the Multitarget Application Router](../90-HANA-Cloud-DB-Dev-MTA-Routes/configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

[Create an Instance of the XS UAA Service](../100-HANA-Cloud-DB-Dev-Security/create-an-instance-of-the-xs-uaa-service-41457ec.md "Use the service broker to create an instance of the xsuaa service.")

[Bind the XS UAA Service Instance to the Multitarget Application](../100-HANA-Cloud-DB-Dev-Security/bind-the-xs-uaa-service-instance-to-the-multitarget-application-a1b87ab.md "You must bind the UAA service instance you create to the multitarget application that is going to use it.")

