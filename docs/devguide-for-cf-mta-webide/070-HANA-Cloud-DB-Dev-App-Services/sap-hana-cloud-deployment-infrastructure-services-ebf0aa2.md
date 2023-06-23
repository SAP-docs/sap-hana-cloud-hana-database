<!-- loioebf0aa26958443f58f86b862056862d4 -->

# SAP HANA Cloud Deployment-Infrastructure Services

The SAP HANA Cloud Deployment Infrastructure service \(HDI\) is the central infrastructure component for application-container management.

The SAP HANA Cloud Deployment Infrastructure \(HDI\) is a service layer of the SAP HANA Cloud database that simplifies the deployment of SAP HANA database objects by providing a declarative approach for defining database objects \(as design-time artifacts\) and ensuring a consistent deployment into the database. The SAP HANA Cloud DI service enables you to create and manage not only HDI containers but also plain schemata, and the Secure Store on shared SAP HANA systems.

The deployment of database objects with HDI is based on a container model where each container corresponds to a database schema. Containers can be used for multiple deployments of the same database artifacts, and for development sandboxes, too. Containers are isolated from each other; each database schema with its deployed database objects is owned by a per-schema technical database user. By default, a cross-container access at the database level is not possible. However, such cross-container access could be granted by means of database privileges.

Database service instances are created by a database-specific service broker, for example, the SAP HANA Cloud database service broker. In the context of the application run time, a database service instance corresponds to a single database schema and an assigned technical database user. The SAP HANA Cloud database service broker delegates schema creation to HDI in such a way that HDI can create its required metadata, database users, and database roles inside the database.

An SAP HANA service instance corresponds to an HDI container or a plain schema on the database. When the service is bound to an application, the bind operation “injects” into the application an application user \(for use by the application code\) and a deployment user \(for user by the database artifact deployer\) to access the container or schmema.



<a name="loioebf0aa26958443f58f86b862056862d4__section_k52_my1_5z"/>

## SAP HANA Service Plans

In the application run time, SAP HANA is exposed as a managed service with the service name “`hana`”. If an application is bound to an instance of the HANA service, the credentials required to access SAP HANA are defined in the application's *<VCAP\_SERVICES\>* environment variable. A tenant database of an SAP HANA instance can be mapped to an Organization or Space in the application run time, and all SAP HANA service instances created within such an Organization or Space relate to a schema in the mapped tenant database.

The following example shows the service plans assosiciated with the `hana` service.

> ### Note:  
> In SAP BTP Cockpit, the "`hana`" service is also known as *SAP HANA Schemas & HDI Containers*. For more information about managing services in SAP BTP cockpit, see *Related Information* below.

> ### Output Code:  
> ```
> $ cf marketplace -e hana
>   
> Getting services from marketplace...
> Getting plans for service "hana"...
>  
> service plan   description                                 free/paid
> –––––––––––––––––––––--––––––––––––––––––––––––––––––––––––---––––––––--
> hdi-shared     HDI container on a HANA database            free
> schema         Schema on a HANA database                   free
> securestore    User with permissions to use secure store   free
> ```



<a name="loioebf0aa26958443f58f86b862056862d4__section_mjz_q1b_5z"/>

## The “hdi-shared” Service Plan

When you create and bind a service instance with the service plan `hdi-shared`, an application receives the credentials required for access to an HDI container, which is basically a database schema that is equipped with additional metadata.

HDI containers ensure isolation, and within an SAP HANA database you can define an arbitrary number of HDI containers. The same objects can be deployed multiple times into different HDI containers in the same SAP HANA database, for example, to install several instances of the same software product in the same SAP HANA database. HDI containers are isolated from each other by means of schema-level access privileges. Cross-container access at the database level is prevented by default, but can be enabled by explicitly granting the necessary privileges, for example, using synonyms. , an application receives the credentials required for access to an HDI container, which is basically a database schema that is equipped with additional metadata.

Database objects \(tables, views, procedures, and so on\) have an owner: the user who created the object. When the owner of a database object is deleted, all objects owned by the deleted user are removed from the database, too. In addition, if application objects are created by end-users, the objects are deleted when the end-user is deleted, for example when the employee leaves the organization. HDI ensures that during deployment all database objects are created by a container-specific technical user, which is never deleted as long as the container exists.

In HDI, database schema content \(for example, tables, views, procedures, etc.\) is defined in corresponding design-time files as part of a development project. These definition artifacts are pushed to the platform as part of a special Node.js application, the HDI Deployer application `@sap/hdi-deploy`, which is part of the run-time platform. This deployer application binds to an SAP HANA service instance and, on start up, creates the set of database objects that correspond to the pushed definition files, for example: `myTable.hdbtable`, `myView.hdbview`, or `myProcedure.hdbprocedure`.

> ### Sample Code:  
> Service-Creation Parameters:
> 
> ```
> {"schema": "<schema-name>", "database_id": "<database_id>"} 
> ```

> ### Note:  
> If no <code>“schema”</code> parameter is used, a random schema name is created and made accessible through *<VCAP\_SERVICES\>* after the service instance is bound to an application. The parameter <code>“database_id”</code> must be used if multiple tenant databases are mapped to the same Cloud Foundry organization or space.

Random schema names is the recommended way to create a service instance; setting a **fixed** schema name creates a global singleton in the database and means that it is not possible to create a service instance with the same schema name.

> ### Sample Code:  
> Service-Binding Parameters:
> 
> ```
> {"roles": "<list of user roles>"} 
> ```

Every time the service instance is bound to an application, the service broker creates a technical application user who is named <code>“user”</code> in the service instance's credentials. The bound application must provide the technical user's credentials when accessing the HDI container's run-time schema. This user is equipped with the service instance's global access role \(<code><i class="varname">&lt;schema-name&gt;</i>::access_role</code>\), where <code><i class="varname">&lt;schema-name&gt;</i></code> is the name of the HDI container schema.

In order to assign roles from the HDI content to the technical application binding user, the HDI deployer implements an automatic assignment of the <code>“default_access_role”</code>, if the role is included in the deployed content. By using the service-binding parameter roles when binding an HDI container to an application, it is possible to declare any role which will be assigned to the technical binding <code>“user”</code>, as illustrated in the following example:

```
$> cf bind-service my-app my-hdi-container -c {"roles": "sap.myapp.roles::read_access_role" }
```

In the application deployment descriptor \(`mtad.yaml`\), this would look like the following code:

> ### Sample Code:  
> Application Deployment Descriptor
> 
> ```json
> ID: com.sap.xs2.samples.my-app
> version: 0.1.0 
> 
> modules: 
>   - name: my-app1 
>     type: javascript.nodejs 
>     requires: 
>       - name: my-hdi-container
>         parameters: 
>           config: 
>             roles: sap.myapp.roles::read_access_role 
> ...
> ```



<a name="loioebf0aa26958443f58f86b862056862d4__section_oqq_s1b_5z"/>

## The “schema” Service Plan

The schema service plan creates a plain schema, which you need to manage manually or with application code. No automated deployment or schema-management services are provided.

You should consider using the schema service plan if your application uses Object-Relational Mapping \(ORM\) tools, for example, those offered by Hibernate or SQLAlchemy, and a framework is available that creates the necessary database resources on demand. The schema service plan could also make sense where applications create and manage their database objects using conventional DDL.

> ### Sample Code:  
> Service Creation Parameters:
> 
> ```json
> {"schema": "<schema-name>", "database_id": "<database_id>"} 
> ```

> ### Note:  
> If no schema parameter is used, a random schema name is created and accessible via *<VCAP\_SERVICES\>* after the service instance is bound to an application. Random schema names is the recommended way to create a service instance; setting a **fixed** schema name creates a global singleton on the database and means that it is not possible to create a service instance with the same schema name.



<a name="loioebf0aa26958443f58f86b862056862d4__section_yj5_s1b_5z"/>

## The “securestore” Service Plan

The `securestore` service plan enables a bound application to make use of stored procedures that provide access to the SAP HANA Secure Store. This functionality is available when using the XS JavaScript `$.security.store` API and allows the bound application not only to insert encrypted values **into** the Secure Store but also to retrieve \(or delete\) encrypted data **from** the Secure Store.

An application that is bound to a `hana` service with the service plan `securestore` can make use of the following stored procedures, which enable access to the SAP HANA Secure Store:

-   `SYS.USER_SECURESTORE_INSERT`

    Insert an encrypted entry into the SAP HANA Secure Store.

-   `SYS.USER_SECURESTORE_RETRIEVE`

    Retrieve an encrypted entry from the SAP HANA Secure Store.

-   `SYS.USER_SECURESTORE_DELETE`

    Delete an encrypted entry from the SAP HANA Secure Store.


> ### Tip:  
> For more information about the parameters required when calling the stored procedures that provide access to the Secure Store, for example, `STORE_NAME`, `KEY`, or `VALUE`, see *Related Information* below.



### Retrieving Values from the SAP HANA Secure Store

When calling the stored procedure `SYS.USER_SECURESTORE_RETRIEVE`, you need to provide the name of the target secure store \(`storename`\) containing the entry to be retrieved, a `key` \(name\) for the retrieved entry, and a binary `value` for the retrieved key. You also need to specify if the retrieved value is stored for the application user \(“`true`”\) or the technical user \(“`false`”\). For more information about the parameters required when calling the procedures that provide access to the Secure Store, see *Related Information* below.

The following code example shows how a Node.js application could make use of the stored procedure `SYS.USER_SECURESTORE_RETRIEVE` to request and obtain encrypted entries from the SAP HANA Secure Store:

> ### Note:  
> To avoid authorization problems when a Node.js application connects to the database, make sure that the resource type for the database connection specified for the MTA's Node.js module \(in the `mta.yaml`\) is `com.sap.xs.hana-securestore`.

> ### Sample Code:  
> Call SYS.USER\_SECURESTORE\_RETRIEVE \(Node.js Application\)
> 
> ```js
> //Secure Store Retrieve
> app.get("/:key?", async(req, res) => { 
>      const hdbext = require("@sap/hdbext"); 
>      const key = req.params.key; 
>      let inputParams = ""; 
>      if (typeof key === "undefined" || key === null) { 
>             res.type("text/plain").status(500).send("ERROR: No Secure Store Key Input Parameter Specified");
>             return; 
>      } else { 
>              inputParams = { 
>                      KEY: key }; 
>      }
>      inputParams.STORE_NAME = "MY_SECURE_STORE";
>      inputParams.FOR_XS_APPLICATIONUSER = true;
>      const client = await getSecureStore();
>      //(client, Schema, Procedure, callback)
>      hdbext.loadProcedure(client, "SYS", "USER_SECURESTORE_RETRIEVE", (err, sp) => {
>           if (err) { 
>                res.type("text/plain").status(500).send(`ERROR: ${err.toString()}`); 
>                return; 
>           } 
>           //(Input Parameters, callback(errors, Output Scalar Parameters, [Output Table Parameters])
>           sp(inputParams, (err, parameters, results) => { 
>                if (err) { 
>                          res.type("text/plain").status(500).send(`ERROR: ${err.message.toString()}`);
>                          return; 
>                } 
>                console.log(`Results: ${parameters.VALUE.toString("utf8")} `);
>                res.type("application/json").status(200).send(`Entry in secure store successsfully retrieved for key: ${key} and value: ${parameters.VALUE.toString("utf8")} `);
>           }); 
>      });
> });
> ```

Bear in mind that, in the Node.js example above, the `KEY` parameter returns a `VALUE` of type `VARBINARY`, which might need to be converted to a character or numeric data type, for example, using `TO_NVARCHAR` on the database side or by using a JavaScript Buffer. The following example code snippet shows how to use a body-parsing module to set the body content used to fill the `VALUE` parameter to `raw`, which ensures that no conversion is required either way \(IN or OUT\):

> ### Sample Code:  
> Process Request Body and Return a JavaScript Buffer
> 
> ```
> module.exports = () => {
> 	const app = express.Router();
> 
> 	const bodyParser = require("body-parser");
> 	app.use(bodyParser.raw({
> 		type: "text/plain"
> 	})); 
> ```

The following code example shows how a Java application could make use of the stored procedure `SYS.USER_SECURESTORE_RETRIEVE` to request and obtain encrypted entries from the SAP HANA Secure Store:

> ### Sample Code:  
> Call SYS.USER\_SECURESTORE\_RETRIEVE \(Java Application\)
> 
> ```java
> @Service 
> public class SecureStoreServiceImpl implements SecureStoreService { 
>     private static final Logger LOGGER = LoggerFactory.getLogger(SecureStoreService.class); 
> 
>     @Autowired
>     @Qualifier("secureStoreDataSource") 
>     private DataSource dataSource; 
> 
>     @Override 
>     public void getValue(String storeName, String key) throws SQLException { 
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
> ```

In the Java example above, the `KEY` parameter for the retrieved entry expects a `VALUE` \(4\) with the BINARY data type. In this case, we ensure the data type is correctly set with `registerOutParameter(4, Types.VARBINARY)`.

**Related Information**  


[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[Core Application Services](core-application-services-b0200e9.md "A selection of essential application services are available with the run-time platform.")

[Maintaining Multitarget Application Services in Cloud Foundry](maintaining-multitarget-application-services-in-cloud-foundry-33e3c59.md "In Cloud Foundry, applications can make use of services managed by a service broker.")

[SAP HANA Secure-Store Interface Procedures and Parameters](../100-HANA-Cloud-DB-Dev-Security/sap-hana-secure-store-interface-procedures-and-parameters-a847b4d.md "A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.")

[Managing Services Using the SAP BTP Cockpit \(SAP Service Manager\)](https://help.sap.com/docs/SERVICEMANAGEMENT/09cc82baadc542a688176dce601398de/cdce096d411242bcbfb9644d0860fd0f.html?version=Cloud)

