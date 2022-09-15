<!-- loio6511bc054b0e48369a625a8019fefd53 -->

# Standard SAP Java Client Libraries for Cloud Foundry

A collection of Java client libraries developed by SAP is provided to help you develop Java applications for Cloud Foundry.



SAP HANA Cloud includes a selection of standard Java libraries, which are available for download from the Maven Central Repository. The libraries include the packages listed in the following table:

> ### Tip:  
> For more detailed information, see the `README` file in the corresponding package or, where available, the JavaDoc reference guide.

<a name="loio6511bc054b0e48369a625a8019fefd53__table_d4f_cw4_dz"/>SAP JAVA Libraries


<table>
<tr>
<th valign="top">

Library



</th>
<th valign="top" align="center">

 [Maven Central](https://search.maven.org/) 



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [`xs-env`](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md#loio6511bc054b0e48369a625a8019fefd53__section_gby_rw4_dz) 



</td>
<td valign="top" align="center">

✔



</td>
<td valign="top">

A utility for setting up and accessing environment variables and services



</td>
</tr>
<tr>
<td valign="top">

 [`java-security`](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md#loio6511bc054b0e48369a625a8019fefd53__section_ors_th3_4mb) 



</td>
<td valign="top" align="center">

✔



</td>
<td valign="top">

A Java wrapper for the security context of authentication for Java applications



</td>
</tr>
<tr>
<td valign="top">

 [`spring-xsuaa`](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md#loio6511bc054b0e48369a625a8019fefd53__section_pmt_th3_4mb) 



</td>
<td valign="top" align="center">

✔



</td>
<td valign="top">

A Java wrapper for the security context of authentication for Spring Boot applications



</td>
</tr>
<tr>
<td valign="top">

 [`java-js-client`](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md#loio6511bc054b0e48369a625a8019fefd53__section_ctf_5w4_dz) 



</td>
<td valign="top" align="center">

✔



</td>
<td valign="top">

A convenient Java wrapper for the Job Scheduler REST API end points



</td>
</tr>
<tr>
<td valign="top">

 [`sap-java-hdi` \(`hdi`\)](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md#loio6511bc054b0e48369a625a8019fefd53__section_mwr_xw4_dz) 



</td>
<td valign="top" align="center">

✔



</td>
<td valign="top">

The SAP HANA Cloud Deployment Infrastructure \(HDI\) client library for Java applications



</td>
</tr>
</table>



<a name="loio6511bc054b0e48369a625a8019fefd53__section_gby_rw4_dz"/>

## xs-env

A utility that enables easy setup of and access to Cloud Foundry environment variables and services.

Objects of type `VcapApplication` store information about applications and objects of type `VcapServices` store information about service instances.

The following example shows how to create `VcapApplication` from the *<VCAP\_APPLICATION\>* system property:

> ### Sample Code:  
> ```
> public static VcapApplication fromSystemProperty() throws IllegalArgumentException {
>        return VcapApplication.from(System.getProperty(VCAP_APPLICATION));
> }
> 
> ```

If the system property is not set, an empty instance is returned. To check if the system property exists, use `getProperty()`, as illustrated in the following example:

```
System.getProperty(VCAP_APPLICATION) != null;
```

The following example shows how to create `VcapApplication` from the *<VCAP\_APPLICATION\>* environment variable.

> ### Sample Code:  
> ```
> public static VcapApplication fromEnvironment() throws IllegalArgumentException {
>        return VcapApplication.from(System.getenv(VCAP_APPLICATION));
> }
> 
> ```

If the environment variable is not set, an empty instance is returned. To check if the environment variable exists, use `getenv()`, as illustrated in the following example:

```
System.getenv().containsKey(VCAP_APPLICATION);
```

The following example shows how to create `VcapServices` from the *<VCAP\_SERVICES\>* system property:

> ### Sample Code:  
> ```
> public static VcapServices fromSystemProperty() throws IllegalArgumentException {
>        return VcapServices.from(System.getProperty(VCAP_SERVICES));
> }
> 
> ```

If the system property is not set, an empty instance is returned. To check if the system property exists, use `getProperty()`, as illustrated in the following example:

```
System.getProperty(VCAP_SERVICES) != null;
```

The following example shows how to create `VcapServices` from the *<VCAP\_SERVICES\>* environment variable:

> ### Sample Code:  
> ```
> public static VcapServices fromEnvironment() throws IllegalArgumentException {
>        return VcapServices.from(System.getenv(VCAP_SERVICES));
> }
> 
> ```

If the environment variable is not set, an empty instance is returned. To check if the environment variable exists, use `getenv()`, as illustrated in the following example:

```
System.getenv().containsKey(VCAP_APPLICATION);
```



<a name="loio6511bc054b0e48369a625a8019fefd53__section_ors_th3_4mb"/>

## java-security

A client library that enables token validation for Java applications in the context of authentication requests on Cloud Foundry run-time environments and with the XS User Account and Authentication service \(XSUAA\).

> ### Tip:  
> The client `java-security` library is intended as a replacement for `java-container-security` for Java applications.



### Configuration

The following example shows how to set up the Maven dependencies for the `java-security` library.

> ### Sample Code:  
> ```
> <dependency> 
>     <groupId>com.sap.cloud.security</groupId> 
>     <artifactId>java-security</artifactId> 
>     <version>2.7.5</version> 
> </dependency> 
> <dependency> 
>     <groupId>org.apache.httpcomponents</groupId> 
>     <artifactId>httpclient</artifactId> 
> </dependency>
> ```



### Usage

1.  Load the service configuration.

    ```
    OAuth2ServiceConfiguration serviceConfig = Environments.getCurrent().getXsuaaConfiguration();
    ```

    > ### Tip:  
    > `Environments` detects the following environments automatically: Cloud Foundry or Kubernetes.

2.  Set up the validators.

    Configure the `JwtValidatorBuilder` once using the service configuration defined in the previous step

    ```
    CombiningValidator<Token> validators = JwtValidatorBuilder.getInstance(serviceConfig).build();
    ```

    > ### Tip:  
    > By default `JwtValidatorBuilder` builds a `CombiningValidator`. For the Signature validation, it needs to fetch the JSON Web Token Keys \(`jwks`\) from the OAuth server. In case the token does not provide a `jku` header parameter, the Open-ID Provider Configuration is also requested from the OAuth Server to determine the `jwks_uri`. The Apache Rest client can be customized via the `JwtValidatorBuilder` builder.

3.  Create a token object.

    This step decodes an encoded JSON Web Token \(JWT\) and parses both the JSON header and the payload. The Token interface provides a simple access to its JWT header parameters and its claims. You can find the claim constants in the \(`TokenClaims`\) class.

    ```
    String authorizationHeader = "Bearer eyJhbGciOiJGUzI1NiJ2.eyJhh..."; 
    Token token = new XsuaaToken(authorizationHeader);
    ```

4.  Validate token to check authentication.

    ```
    ValidationResult result = validators.validate(token); 
    
    if(result.isErroneous()) { 
       logger.warn("User is not authenticated: " + result.getErrorDescription()); 
    }
    ```

5.  Cache the validated token \(thread-locally\).

    ```
    SecurityContext.setToken(token);
    ```

6.  Retrieve information from the token.

    ```
    Token token = SecurityContext.getToken(); 
    
    String email = token.getClaimAsString(TokenClaims.EMAIL); 
    List<String> scopes = token.getClaimAsStringList(TokenClaims.XSUAA.SCOPES); 
    java.security.Principal principal = token.getPrincipal(); 
    Instant expiredAt = token.getExpiration(); 
    ...
    ```

7.  Display information stored in `VCAP_SERVICES`

    If you need further details from the `VCAP_SERVICES` system environment variable, which are not exposed by `OAuth2ServiceConfiguration` interface you can use the `DefaultJsonObject` class for JSON parsing.

    ```
    String vcapServices = System.getenv(CFConstants.VCAP_SERVICES); 
    JsonObject serviceJsonObject = new DefaultJsonObject(vcapServices).getJsonObjects(Service.XSUAA.getCFName()).get(0);
    Map<String, String> xsuaaConfigMap = serviceJsonObject.getKeyValueMap(); 
    Map<String, String> credentialsMap = serviceJsonObject.getJsonObject(CFConstants.CREDENTIALS).getKeyValueMap();
    ```


> ### Note:  
> For more information about the `java-security` library, see *SAP CP Java Security Library \(GitHub\)* in *Related Information* below.



<a name="loio6511bc054b0e48369a625a8019fefd53__section_pmt_th3_4mb"/>

## spring-xsuaa

A client library that enables token validation for Java applications in the context of authentication requests.

> ### Tip:  
> The client `spring-xsuaa` library is intended as a replacement for `java-container-security` for Spring Boot applications.



### Configuration

The following example shows how to set up the Maven dependencies for the `spring-xsuaa` library.

> ### Sample Code:  
> ```
> 
> <dependency> <!-- includes spring-security-oauth2 --> 
>     <groupId>org.springframework.security</groupId> 
>     <artifactId>spring-security-oauth2-jose</artifactId> 
> </dependency> 
> <dependency> 
>     <groupId>org.springframework.security</groupId> 
>     <artifactId>spring-security-config</artifactId> 
> </dependency> 
> <dependency> 
>     <groupId>org.springframework.security</groupId> 
>     <artifactId>spring-security-oauth2-resource-server</artifactId> 
> </dependency> 
> <dependency> 
>     <groupId>com.sap.cloud.security.xsuaa</groupId> 
>     <artifactId>spring-xsuaa</artifactId> <version>2.7.5</version> 
> </dependency> 
> <dependency> <!-- new with version 1.5.0 --> 
>     <groupId>org.apache.logging.log4j</groupId> 
>     <artifactId>log4j-to-slf4j</artifactId> 
>     <version>2.11.2</version> 
> </dependency>
> ```

You can also use the `xsuaa-spring-boot-starter` to set up automatic configuration, as shown in the following example:

```
<dependency> 
    <groupId>com.sap.cloud.security.xsuaa</groupId> 
    <artifactId>xsuaa-spring-boot-starter</artifactId>
    <version>2.7.5</version> 
</dependency>
```



### Usage

Spring Boot Applications can use cloud the `spring-xsuaa` client library to perform the offline token validation of a JSON Web Token \(JWT\). The signature is validated using the token keys received from the `XSUAA` service. To configure Spring security for your Spring Boot application, perform the following steps:

1.  Access user or token information.

    In the Java coding, use the token to extract user information:

    ```
    @GetMapping("/getGivenName") 
    public String getGivenName(@AuthenticationPrincipal Token token) { 
        return token.getGivenName(); }
    ```

2.  Check authorization within a method.

    ```
    @GetMapping(@AuthenticationPrincipal Token token) 
    public ResponseEntity<YourDto> readAll() { 
         if (!token.getAuthorities().contains(new SimpleGrantedAuthority("Display"))) { 
             throw new NotAuthorizedException("This operation requires \"Display\" scope"); 
         } 
    } 
    ... 
    @ResponseStatus(HttpStatus.FORBIDDEN) //set status code to '403' 
    class NotAuthorizedException extends RuntimeException { 
        public NotAuthorizedException(String message) { 
            super(message); 
        } 
    }
    ```

3.  Check authorization at the **method** level.

    Spring Security supports authorization semantics at the method level. As a prerequisite, you need to enable global Method Security:

    ```
    @GetMapping("/hello-token") 
    @PreAuthorize("hasAuthority('Display')") 
    public Map<String, String> message() { 
        ... 
    }
    ```


> ### Note:  
> For more information, see *SAP CP Spring XSUAA Security Library* in *Related Information* below.



<a name="loio6511bc054b0e48369a625a8019fefd53__section_ctf_5w4_dz"/>

## java-js-client

This client library is a Java wrapper that enables convenient access to the Job Scheduler's REST API end points. The Job Scheduler service enables consumers to create, schedule, manage, and monitor application tasks within the Cloud Foundry application run-time.



### Usage

The following code shows how to obtain an instance of the `SchedulerClient` from the factory:

```
Client client = SchedulerFactory.getSchedulerClient();
```

You must set the `jobscheduler` credentials to the client, as illustrated in the following code example:

```
client.setApi("https://host.acme.com:4242"); 
client.setUserName("a9a32ac0-5522-11e5-adbd-13adbfaf2ac7"); 
client.setPassword("6081473c-6563-43ca-a8dd-61abb987330f");
```

To enable the client to consume the scheduler API, you must create an instance of the `SchedulerManager`, as illustrated in the following example:

```
SchedulerManager schedulerManager = client.getSchedulerManager();
```

The following example shows how to **update** a scheduled job:

```
newJob.setActive(false); 
newJob.setUser("test"); 
newJob.setPassword("Toor1234"); 

try { 
    newJob = (Job) schedulerManager.update(newJob); 
    slf4jLogger.info("Job is updated. Now, the job is " + (newJob.getActive() ? "active" : "inactive")); 
} catch (SchedulerException e) { 
    slf4jLogger.error("Failed to update the job"); 
}
```

The following example shows how to **add** a new schedule to an existing job and **update** a schedule:

```
// Create new schedule entity 
Schedule newSchedule = new Schedule(); 
newSchedule.setDescription("Ping Google every 20 minutes using xscron"); 
newSchedule.setCron("* * * * * */20 *"); 
newSchedule.setJob(newJob); 

try { 
    Schedule createdSchedule = (Schedule) schedulerManager.create(newSchedule); 
    slf4jLogger.info("New schedule is created with id " + createdSchedule.getId()); 

    // --------------Update schedule---------- 
    createdSchedule.setStartTime(startTime); 
    createdSchedule.setEndTime(endTime); 
    Schedule schedule2 = (Schedule) schedulerManager.update(createdSchedule); 
    slf4jLogger.info("schedule updated with start time " 
      + schedule2.getStartTime().getDate() + " end time " 
      + schedule2.getEndTime().getDate()); 

    newJob = schedulerManager.searchJobById(newJob.getId()); 
    slf4jLogger.info("Now, the number of schedules is " + newJob.getSchedules().size());
} catch (SchedulerException e) { 
    slf4jLogger.error("Failed to update the schedule"); 
}
```

The following example shows how to **activate** or **deactivate** all schedules configured for a job:

```
try { 
    schedulerManager.activateAllSchedules(newJob); 
    Collection<Schedule> schedules = newJob.getSchedules(); 
    boolean scheduleActive = false; 
    for (Iterator<Schedule> scheduleIterator = schedules.iterator(); scheduleIterator.hasNext();) { 
         Schedule schedule2 = (Schedule) scheduleIterator.next(); 
         scheduleActive = scheduleActive & schedule2.getActive(); 
    } 
    slf4jLogger.info("All the schedules are now " + (scheduleActive == true ? "active" : "inactive")); 
} catch (SchedulerException e1) { 
    slf4jLogger.error("Failed to activate the schedules"); 
} 

try { 
    schedulerManager.deactivateAllSchedules(newJob); 
    newJob = schedulerManager.searchJobById("90009"); 
    slf4jLogger.info("All schedules are deleted. The number of schedules is " + newJob.getSchedules().size()); 
} catch (SchedulerException e1) { 
    slf4jLogger.error("Failed to deactivate the schedules"); 
}
```

The following example shows how to **delete** a scheduled job:

```
try { 
    schedulerManager.delete(newJob); 
    slf4jLogger.info("The job is deleted"); 
} catch (SchedulerException e) { 
    slf4jLogger.error("Failed to delete the job"); 
}
```

The following example shows how to **update** a log:

```
    Log log = new Log(); 
    log.setJobId("1"); 
    log.setScheduleId("da722278-0a22-440c-a4d6-c599b77617f4"); 
    log.setId("11765A573A618A79E10000000A61A17B"); 
    log.setMessage("New log updated"); 
    log.setSuccess(true); 
    Log newLog = new Log(); 
try { 
    newLog = (Log) schedulerManager.update(log); 
    slf4jLogger.info("Log is Updated "); 
} catch (SchedulerException e2) { 
    slf4jLogger.error("Failed to update the log"); 
} 
```
```



<a name="loio6511bc054b0e48369a625a8019fefd53__section_mwr_xw4_dz"/>

## sap-java-hdi \(hdi\)

The `sap-java-hdi` \(`hdi`\) client library enables Java applications to access the SAP HANA Cloud Deployment Infrastructure \(HDI\).



### sap-java-hdi \(version 2.\*\)

Version 2.\* of the SAP HANA DI \(HDI\) client library for Java applications wraps the HDI SQL APIs in Java classes and methods. The following main classes are available:

<a name="loio6511bc054b0e48369a625a8019fefd53__table_ehb_txl_h1b"/>HDI JAVA Classes


<table>
<tr>
<th valign="top">

Class



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `HDI` 



</td>
<td valign="top">

Provides access to the `_SYS_DI` API



</td>
</tr>
<tr>
<td valign="top">

 `Container` 



</td>
<td valign="top">

Provides access to the API of a specific HDI container



</td>
</tr>
<tr>
<td valign="top">

 `ContainerGroup` 



</td>
<td valign="top">

Provides access to the API of a specific HDI container group



</td>
</tr>
</table>

> ### Tip:  
> For reasons of support and compatibility, it is recommended to use version 2.\* of `sap-java-hdi` client library.

To use all APIs, the connected user must have the following privileges:

-   `EXECUTE`

    The `EXECUTE` privilege is required for the corresponding SQL procedures.

-   `SELECT`

    The `SELECT` privilege is required for all table types in `SYS_DI` \(`TT*`\).


> ### Note:  
> For all the examples used in this section to illustrate some of the most common usage scenarios for the HDI Java client library `sap-java-hdi`, it is assumed that the `hdiUser` has the privileges required to access `_SYS_DI`. In addition, some APIs require a minimum SAP HANA Cloud version. For more information about which SAP HANA Cloud version is required by a specific class or method, see the `sap-java-hdi` JavaDoc reference.

The following example shows how to use `sap-java-hdi` to instantiate an HDI API wrapper object for the database “`DB1`” in the SAP HANA Cloud instance running on a host named “`someHost`” on SQL port `30015` with the user “`hdiUser`”, the password “`Abcd1234`” and, in addition, using the user's default schema for temporary tables.

```
HDI hdi = new HDI("someHost", "30015", "DB1", "hdiUser", "Abcd123", "hdiUser");
```

To create a new container group named “`someGroup`”, use the following code:

> ### Tip:  
> The last argument \(“`null`” in this case\) is an optional list of key-value parameters for the call.

```
ResultTuple rt = hdi.createContainerGroup("someGroup", null);
System.out.println("Return code: " + rt.getRC());
System.out.println("Messages: " + rt.getMessages());
```

The following example shows how to grant the default container-group administrator privileges for “`someGroup`” to the user “`hdiUser`”:

```
List<APIPrivilege> groupAdminPrivileges = hdi.getDefaultContainerGroupAdminPrivileges("", "hdiUser");
rt = hdi.grantContainerGroupApiPrivileges("someGroup", groupAdminPrivileges, null); 
```

The following code shows how to use the `sap-java-hdi` to instantiate a container-group-API wrapper object for “`someGroup`” in the database “`DB1`” in the SAP HANA Cloud instance running on host “`someHost`” with SQL port `30015` with user `hdiUser`, password `Abcd1234` and using the user's default schema for temporary tables:

```
ContainerGroup group = new ContainerGroup("someGroup", "someHost", "30015", "DB1", "hdiUser", "Abcd123", "hdiUser"); 
```

The following example shows how to create a new container named “`someContainer`” with the Java HDI API and place it in the container group “`someGroup`” created in the previous example:

> ### Tip:  
> The API object “`group`” used in this example was created for the container group “`someGroup`”\(`= new ContainerGroup("someGroup", [...])`\)

```
rt = group.createContainer("someContainer", null);
```

To grant the default container-administrator privileges for the HDI container “`someContainer`” to the HDI user “`hdiUser`”, consider the following functions:

```
List<APIPrivilege> containerAdminPrivileges = group.getDefaultContainerAdminPrivileges("", "hdiUser");
rt = group.grantContainerApiPrivileges("someContainer", containerAdminPrivileges, null);
```

The following functions show how to use the HDI container API to instantiate a container-API wrapper object for `someContainer` in database `DB1` in the SAP HANA Cloud instance running on host `someHost` with SQL port `30015` with user `hdiUser`, password `Abcd1234`, and using the user's default schema to store temporary tables:

```
Container container = new Container("someContainer", "someHost", "30015", "DB1", "hdiUser", "Abcd123", "hdiUser"); 
```

To list the plug-in libraries configured in `someContainer`, consider the following functions:

```
LibraryInformationResultTuple lrt = container.listConfiguredLibraries(null); 
System.out.println("Configured libraries: " + lrt.getResults()); 
```

**Related Information**  


[Download and Consume Java Libraries](download-and-consume-java-libraries-8783c06.md "A selection of SAP-specific and ready-to-use Java client libraries is available for download from the Maven Central Repository.")

[The Cloud Foundry Java Run Time](the-cloud-foundry-java-run-time-2b5a9a4.md "SAP Business Technology Platform provides a Cloud Foundry Java run time to which you can deploy your Java applications.")

[SAP CP Java Security Library \(GitHub\)](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/java-security#configuration)

[SAP CP Spring XSUAA Library \(GitHub\)](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/spring-xsuaa)

[Maven Central Repository](https://mvnrepository.com/search?q=SAP&d=com.sap)

