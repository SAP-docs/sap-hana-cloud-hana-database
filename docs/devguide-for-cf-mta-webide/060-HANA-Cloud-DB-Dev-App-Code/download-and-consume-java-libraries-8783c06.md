<!-- loio8783c06f6d5a48e791e7ad17d49a95c0 -->

# Download and Consume Java Libraries

A selection of SAP-specific and ready-to-use Java client libraries is available for download from the Maven Central Repository.



<a name="loio8783c06f6d5a48e791e7ad17d49a95c0__prereq_p5j_wy4_dz"/>

## Prerequisites

You have installed Maven on your development system.



## Context

To use the SAP Java Client libraries, perform the following steps:



## Procedure

1.  Configure the required library dependencies in your Java application's `pom.xml` file.

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

    For more information about locating individual SAP Java libraries on Maven Central, see *Related Information* below.

2.  Run a Maven build.

    Navigate to the folder in your local file system where you extracted the Java client libraries and run a Maven build with the following command:

    ```
    mvn clean install
    ```

    The Java client libraries are installed in the local Maven repository from where they can be consumed by your Maven project.


**Related Information**  


[Standard SAP Java Client Libraries for Cloud Foundry](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md "A collection of Java client libraries developed by SAP is provided to help you develop Java applications for Cloud Foundry.")

[Tutorials: Setting Up the Java Run-Time Environment for Cloud Foundry](tutorials-setting-up-the-java-run-time-environment-for-cloud-foundry-3e37f7b.md "A selection of tutorials that show you how to set up an application to run in Cloud Foundry's Java run-time environment on SAP Business Technology Platform.")

[Maven Central Repository](https://mvnrepository.com/search?q=SAP&d=com.sap)

