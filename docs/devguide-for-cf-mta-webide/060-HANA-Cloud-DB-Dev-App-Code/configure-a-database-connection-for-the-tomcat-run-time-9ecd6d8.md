<!-- loio9ecd6d8b54b645b394672ab5c45a9156 -->

# Configure a Database Connection for the Tomcat Run Time

Configure a data source for Tomcat.



<a name="loio9ecd6d8b54b645b394672ab5c45a9156__context_azc_zn2_dhb"/>

## Context

The steps below demonstrate how data sources can be configured in such a way that a developer or operator can change the SAP HANA Cloud service used for creating the data source without having to rebuild or release a new version of the application archive.



<a name="loio9ecd6d8b54b645b394672ab5c45a9156__steps_c45_v5x_3v"/>

## Procedure

1.  Create a `context.xml` file.

    The `context.xml` file has to be inside the `META-INF/` directory of the application's WAR file and has to contain information about the data source to be used.

    > ### Example:  
    > Sample `context.xml`
    > 
    > ```
    > 
    > <?xml version='1.0' encoding='utf-8'?>
    > 
    > <Context>
    >  <Resource name="jdbc/DefaultDB"
    >     auth="Container"
    >     type="javax.sql.DataSource"
    >     factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
    >     service="${service_name_for_DefaultDB}"/>
    > </Context>
    > 
    > ```

    In this example a placeholder is used for the service instance name.

2.  Add the default keys and their values.

    You need to include the data source information in `META-INF/sap_java_buildpack/config/resource_configuration.yml` of the WAR file to define a default value for the placeholder from the previous step.

    > ### Example:  
    > Defining a default service in `resource_configuration.yml`
    > 
    > ```
    > 
    > ---
    >  tomcat/webapps/ROOT/META-INF/context.xml:
    >   service_name_for_DefaultDB: di-core-hdi
    > 
    > ```

    This configuration ensures that the service used for the creation of data sources is determined while staging, and *di-core-hdi* is used. To use this method to change the data sources without having to rebuild or make a new release of the application, developers or operators need to perform an additional deployment of the same application archive.

3.  Add the key values to be updated.

    To use a different service instance, you need to provide an environment variable in the `manifest.yml` file and bind the application to that service instance in the services section of the `manifest.yml` file.

    > ### Example:  
    > Defining a new service for the look-up of the data source
    > 
    > ```
    > 
    > env:
    >   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/META-INF/context.xml': {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}]"
    > 
    > ```

    Using this configuration, when the application starts, the factory named `com.sap.xs.jdbc.datasource.TomcatDataSourceFactory` takes the parameters bound to service *my-local-special-di-core-hdi* from the environment, creates a data source, and binds it under `jdbc/DefaultDB`. The application then uses the Java Naming and Directory Interface \(JNDI\) to look up how to connect with the database.


**Related Information**  


[Configure a Database Connection](configure-a-database-connection-d462ffc.md "You can configure your application to use a database connection so that the application can persist its data.")

[Database Connection Configuration Details](database-connection-configuration-details-79d5638.md "Define details of the database connection used by your multitarget Java application in Cloud Foundry.")

[SAP HANA Cloud HDI Data Source](sap-hana-cloud-hdi-data-source-29639df.md "Set up HDI data sources for multitarget Java applications in SAP HANA Cloud.")

