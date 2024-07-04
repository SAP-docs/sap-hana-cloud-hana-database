<!-- loio8783c06f6d5a48e791e7ad17d49a95c0 -->

# Download and Consume Java Libraries

A selection of SAP-specific and ready-to-use Java client libraries is available for download from the Maven Central Repository.



<a name="loio8783c06f6d5a48e791e7ad17d49a95c0__prereq_aqd_c2x_y1c"/>

## Prerequisites

-   You have installed Maven on your development system.
-   You have access to the Maven Central repository



<a name="loio8783c06f6d5a48e791e7ad17d49a95c0__context_cqd_c2x_y1c"/>

## Context

To download the SAP Java Client libraries, perform the following steps:

> ### Note:  
> If you do not want to download the libraries for local use, the standard SAP Java libraries are also available on the Maven Central Repository. For more details, see *Related Information* below.



<a name="loio8783c06f6d5a48e791e7ad17d49a95c0__steps_dqd_c2x_y1c"/>

## Procedure

1.  Download the package containing the library you need.

    > ### Note:  
    > The most recent versions of the SAP Java client libraries are available for download on Maven Central, which is the default and recommended source for Java libraries provided by SAP. For more information, see *Related Information* below.

    For more information about locating individual SAP Java libraries on Maven Central, see *Related Information* below.

2.  Extract the contents of the library you download from Maven Central into a folder in your local file system.

3.  Run a Maven build.

    Navigate to the folder in your local file system where you extracted the Java client libraries and run a Maven build with the following command:

    ```
    mvn clean install
    ```

    The Java client libraries are installed in the local Maven repository from where they can be consumed by your Maven project.


**Related Information**  


[Standard SAP Java Client Libraries for Cloud Foundry](standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md "A collection of Java client libraries developed by SAP is provided to help you develop Java applications for Cloud Foundry.")

[Tutorials: Setting Up the Java Run-Time Environment for Cloud Foundry](tutorials-setting-up-the-java-run-time-environment-for-cloud-foundry-3e37f7b.md "A selection of tutorials that show you how to set up an application to run in Cloud Foundry's Java run-time environment on SAP Business Technology Platform.")

[Maven Central Repository](https://mvnrepository.com/search?q=SAP&d=com.sap)

