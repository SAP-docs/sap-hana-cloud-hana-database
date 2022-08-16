<!-- loio9210fd0996804d4dbfdd7d341048c766 -->

# Access the SAP HANA Secure Store with Java

Use a Java application to maintain entries in the SAP HANA Secure Store.



<a name="loio9210fd0996804d4dbfdd7d341048c766__prereq_yrs_ybb_fcb"/>

## Prerequisites

To maintain content in the SAP HANA Secure Store, bear in mind the following conditions:

-   The multitarget application must be bound to an instance of the `hana` service using the `securestore` service plan.

-   The resource type for the database connection specified in the MTA's deployment descriptor \(`mta.yaml` file\) must be `com.sap.xs.hana-securestore`.




<a name="loio9210fd0996804d4dbfdd7d341048c766__context_zjg_kcb_mgb"/>

## Context

In the context of the application run time, the SAP HANA Secure Store is used to maintain sensitive information such as user credentials. Access to the SAP HANA Secure Store is enabled by stored procedures which you can use to insert, retrieve, and delete entries in the Secure Store. Any application that is bound to an instance of the `hana` service with the service plan `securestore` has access to these stored procedures and can use them to maintain content stored in the Secure Store.

> ### Tip:  
> For more information about the parameters required when calling the Secure-Store procedures, see *Related Information* below.

The following examples show how to use a Java application to maintain entries programmatically in the SAP HANA Secure Store:



<a name="loio9210fd0996804d4dbfdd7d341048c766__steps_okg_kcb_mgb"/>

## Procedure

1.  Insert encrypted values into the SAP HANA Secure Store.

    The following example shows how to use a Java application to insert encrypted entries into the SAP HANA Secure Store; the `SecureStoreService` is configured in another file:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_INSERT \(Java Application\)
    > 
    > ```
    > package bla.bla.test.securestore.service;
    > 
    > import java.sql.CallableStatement;
    > import java.sql.Connection;
    > import java.sql.SQLException;
    > import java.sql.Types;
    > 
    > import javax.sql.DataSource;
    > 
    > import org.slf4j.Logger;
    > import org.slf4j.LoggerFactory;
    > import org.springframework.beans.factory.annotation.Autowired;
    > import org.springframework.beans.factory.annotation.Qualifier;
    > import org.springframework.stereotype.Service;
    > 
    > @Service 
    > public class SecureStoreServiceImpl implements SecureStoreService { 
    >     private static final Logger LOGGER = LoggerFactory.getLogger(SecureStoreService.class); 
    > 
    >     @Autowired
    >     @Qualifier("secureStoreDataSource") 
    >     private DataSource dataSource; 
    >     
    >     @Override 
    >     public void writeValue(String storeName, String key, String value) throws SQLException {
    >        LOGGER.info("secure store write value: " + storeName + " / " + key + " / " + value); 
    >     
    >        this.deleteValue(storeName, key); 
    > 
    >        try (Connection connection = dataSource.getConnection()) { 
    >     
    >        CallableStatement callableStatement = connection
    >                         .prepareCall("{call SYS.USER_SECURESTORE_INSERT(?,?,?,?)}"); 
    >        callableStatement.setString(1, storeName); 
    >        callableStatement.setBoolean(2, false); 
    >        callableStatement.setString(3, key); 
    >        callableStatement.setBytes(4, value.getBytes()); 
    >        callableStatement.executeUpdate(); 
    >        }
    >     } 
    > ```

    In the Java example above, the `KEY` parameter for the inserted entry expects a `VALUE` \(4\) with the BINARY data type, so any hard-coded values \(numbers, dates, strings\) in the `INSERT` call need to be converted. In this case, we ensure the data type is correctly set with `setBytes(4, value.getBytes())`.

2.  Retrieve encrypted values from the SAP HANA Secure Store.

    The following example shows how to use a Java application to retrieve encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_RETRIEVE \(Java Application\)
    > 
    > ```
    > @Override 
    > public void getValue(String storeName, String key) throws SQLException { 
    >        LOGGER.info("secure store read value: " + storeName + " / " + key); 
    > 
    >        try (Connection connection = dataSource.getConnection()) { 
    >     
    >        CallableStatement callableStatement = connection
    >                          .prepareCall("{call SYS.USER_SECURESTORE_RETRIEVE(?,?,?,?)}"); 
    >        callableStatement.setString(1, storeName); 
    >        callableStatement.setBoolean(2, false); 
    >        callableStatement.setString(3, key);
    >        callableStatement.registerOutParameter(4, Types.VARBINARY);
    >        
    >        callableStatement.executeUpdate();
    > 
    >        byte[] bytes = callableStatement.getBytes(4);
    >  
    >        if (null == bytes) { 
    >               LOGGER.info("value is null");
    >               return null; 
    > 
    >        } else { 
    >               String returnValue = new String(bytes); 
    >               LOGGER.info("return value is :" + returnValue); 
    > 
    >               return returnValue; 68 } 
    >        }
    >     }
    > } 
    > ```

    In the Java example above, the `KEY` parameter returns a `VALUE` \(4\) with the VARBINARY data type. In this example, we ensure the data type for the OUT parameter is correctly set with `registerOutParameter(4, Types.VARBINARY)`.

3.  Delete encrypted values from the SAP HANA Secure Store.

    The following example shows how to use a Java application to remove encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_DELETE \(Java Application\)
    > 
    > ```
    > @Override 
    > public void deleteValue(String storeName, String key) throws SQLException { 
    >        LOGGER.info("secure store delete value: " + storeName + " / " + key); 
    > 
    >        try (Connection connection = dataSource.getConnection()) { 
    >     
    >        CallableStatement callableStatement = connection
    >                          .prepareCall("{call SYS.USER_SECURESTORE_DELETE(?,?,?)}"); 
    >        callableStatement.setString(1, storeName); 
    >        callableStatement.setBoolean(2, false); 
    >        callableStatement.setString(3, key); 
    >        
    >        callableStatement.executeUpdate(); 
    >        }
    >     }
    > ```

4.  Set up a secure connection to the SAP HANA Secure Store.

    To avoid authorization problems when the application tries to connect to the database, it is essential to ensure that the resource type for the database connection specified in the MTA's development descriptor \(`mta.yaml` file\) is `com.sap.xs.hana-securestore`.

    1.  Add a new secure-connection resource type to the MTA's development descriptor.

        To ensure a secure connection to the database, we use an instance of the `hana` service with the service plan `securestore`. For this, we need to define a corresponding resource in the application's development descriptor \(`MTA.yaml`\), and specify that it is required by the Java module using it, as illustrated in the following \(**incomplete**\) code snippet:

        > ### Sample Code:  
        > Resources in the Development Descriptor \(`MTA.yaml`\) of a Java Application
        > 
        > ```
        > ID: MySecureStoreApp
        > _schema-version: '2.0'
        > version: 1.0.0
        > modules:
        >   - name: srv 
        >     type: java 
        >     path: srv 
        >     requires: 
        >       - name: MyDBConnection-secure
        >     provides: 
        >       - name: srv_api 
        >         properties: 
        >           url: '${default-url}'
        > resources:
        >   - name: openSAPHANA-hdi-container
        >     properties: 
        >       hdi-container-name: '${service-name}' 
        >     type: com.sap.xs.hdi-container 
        >   - name: openSAP-ex-uaa 
        >     type: com.sap.xs.uaa-space 
        >     parameters: 
        >       path: ./xs-security.json
        >   - name: MyDBConnection-secure
        >     type: com.sap.xs.hana-securestore
        > ```

    2.  Initialize a connection to the Secure Store resource.

        The following Java code example shows how to use the name of the `securestore` service instance to create the data source for the connection to the SAP HANA secure store:

        > ### Sample Code:  
        > Connect the XS Java Application to the Secure-Store Service-Instance
        > 
        > ```
        > package bla.bla.test.securestore.configuration; 
        > 
        > import javax.sql.DataSource; 
        > 
        > import org.springframework.cloud.config.java.AbstractCloudConfig; 
        > import org.springframework.context.annotation.Bean; 
        > import org.springframework.context.annotation.Configuration; 
        > 
        > @Configuration 
        > public class CloudServiceConfig extends AbstractCloudConfig { 
        >        @Bean public DataSource secureStoreDataSource() { 
        > 
        >              // use service-instance name to create the data source 
        >              return connectionFactory().dataSource("hana-securestore"); 
        > } 
        > 
        >        @Bean public DataSource schemaDataSource() { 
        > 
        >              // use service-instance name to create the data source 
        >              return connectionFactory().dataSource("hana-schema");
        >        }
        > }
        > ```

    3.  Manage the requests to access the secure store service.

        The following code example shows how the Java application controls the `POST`, `GET`, and `DELETE` requests used to insert, retrieve, and delete entries in the SAP HANA secure store:

        > ### Sample Code:  
        > Control Access to the Java Application's Secure-Store Service Instance
        > 
        > ```
        > package bla.bla.test.securestore.controller;
        > 
        > import java.sql.SQLException;
        > 
        > import org.springframework.beans.factory.annotation.Autowired;
        > import org.springframework.web.bind.annotation.DeleteMapping;
        > import org.springframework.web.bind.annotation.GetMapping;
        > import org.springframework.web.bind.annotation.PostMapping;
        > import org.springframework.web.bind.annotation.RequestMapping;
        > import org.springframework.web.bind.annotation.RestController;
        > 
        > import bla.bla.test.securestore.service.SecureStoreService;
        > 
        > @RestController
        > @RequestMapping("/securestore")
        > public class SecureStoreController {
        > 
        > 	@Autowired
        > 	private SecureStoreService secureStoreService;
        > 
        > 	@PostMapping
        > 	public void setValue() throws SQLException {
        > 		secureStoreService.writeValue("store", "key", "value");
        > 	}
        > 
        > 	@GetMapping
        > 	public String get() throws SQLException {
        > 		return secureStoreService.getValue("store", "key");
        > 	}
        > 
        > 	@DeleteMapping
        > 	public void delete() throws SQLException {
        > 		secureStoreService.deleteValue("store", "key");
        > 	}
        > }
        > ```



**Related Information**  


[SAP HANA Secure-Store Interface Procedures and Parameters](sap-hana-secure-store-interface-procedures-and-parameters-a847b4d.md "A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.")

[Access the SAP HANA Secure Store with Node.js](access-the-sap-hana-secure-store-with-node-js-be4db00.md "Use a Node.js application to maintain entries in the SAP HANA Secure Store.")

[Access the SAP HANA Secure Store with SQL](access-the-sap-hana-secure-store-with-sql-1dee8a9.md "Use SQL to maintain entries the SAP HANA Secure Store.")

