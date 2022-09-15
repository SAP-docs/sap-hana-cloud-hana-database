<!-- loio32e95901db054e5e916dd25a5020bcdf -->

# Writing the Multitarget Application Code

Add business logic to your multitarget application to enable it to work with the database artifacts.

The business logic is used to help retrieve data from the database, for example, using OData services. The data is requested from and displayed in the client user interface.

The Cloud Foundry run-time platform provides a number of services for managing the various container instances and their application run times. Containers are used to manage run times and allow for isolation, resource management, and shared service injection. The application run times are lightweight processes that are invoked over HTTP and communicate remotely with the database. Execution environments such as JavaScript, including Node.js, and Java are supported.

The application services can be used to expose the database data model, with its tables, views and database procedures, to clients. This can be done in a declarative way using OData services or by writing native application-specific code that runs in the SAP HANA Cloud context. You can also build dynamic HTML5 UI applications.



## JavaScript Applications

For applications written in JavaScript \(Node.js or XS JavaScript\), you would typically expect the following design-time file structure:

> ### Sample Code:  
> ```
> JavaScript-AppName
> |- db/                          # Database artifacts
> |  |- package.json            
> |  |- src/                    
> |     |- .hdiconfig           
> |     |- mytable.hdbtable
> |     \- myview.hdbview  
> |      
> |- js/                          # JavaScript artifacts
> |  |- server.js                 # JavaScript application entry point
> |  |- package.json              # JavaScript application details/dependencies
> |  \- lib/                      # JavaScript source code
> |  \- node_modules/             # Downloaded node module packages
> | 
> |- ui/ 
> |  |- xs-app.json               # Application-router configuration
> |  |- package.json  
> |  \- resources/        
> |
> |- xs-security.json
> |- package.json
> \- mtad.yaml     
> 
> ```

-   Add a package description file \(`package.json`\) to your JavaScript resource-files folder with details of your application's contents and dependencies.

-   Add a start-up file for your JavaScript application, for example, `main.js`.

-   Create express routes.

-   Create JavaScript source files \(`.js` or `.xsjs`\). These files must be placed in the corresponding application module's folder, for example, `js/src/*.js` or `xsjs/src/*.xsjs`.




<a name="loio32e95901db054e5e916dd25a5020bcdf__section_efr_2wt_tt"/>

## Java Applications

For applications written in Java, a multi-target application would typically have the following design-time structure:

> ### Sample Code:  
> ```
> Java-AppName
> |- db/                          # Database artifacts
> |  |- package.json   
> |  |- src/                    
> |     |- .hdiconfig           
> |     |- mytable.hdbtable
> |     \- myview.hdbview        
> |
> |- java/                        # Java artifacts
> |  |- pom.xml                   # Java project object model (Maven)
> |  \- src/                      # Java source code
> |
> |- ui/ 
> |  |- xs-app.json               # Application-router configuration
> |  \- resources/
> |
> |- xs-security.json        
> |- package.json
> \- mtad.yaml     
> 
> ```

-   Write the Java application's code. These files must be placed in the corresponding application module's folder, for example,`java/src/*`

-   Look up the required data-source.

-   Build the WAR file based on the project object model file \(pom.xml\), for example, with Maven.




<a name="loio32e95901db054e5e916dd25a5020bcdf__section_drl_5rt_5fb"/>

## Python Applications

For applications written in Python, a multi-target application would typically have the following design-time structure:

> ### Sample Code:  
> ```
> Python-AppName
> |- db/                         # Database artifacts
> |  |- package.json   
> |  |- src/                    
> |     |- .hdiconfig           
> |     |- mytable.hdbtable
> |     \- myview.hdbview        
> |
> |- pyapp/                      # Python artifacts
> |  |- runtime.txt              # Python app run-time version declaration
> |  |- requirements.txt         # Python app dependencies list
> |  |- manifest.yml             # Python app build/deploy description
> |  \- server.py                # Application logic
> 
> |
> |- ui/ 
> |  |- xs-app.json              # Application-router configuration
> |  \- resources/
> |
> |- xs-security.json        
> |- package.json
> \- mtad.yaml     
> 
> ```

**Related Information**  


[The Cloud Foundry JavaScript Run Time](the-cloud-foundry-javascript-run-time-18c0192.md "Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.")

[The Cloud Foundry Java Run Time](the-cloud-foundry-java-run-time-2b5a9a4.md "SAP Business Technology Platform provides a Cloud Foundry Java run time to which you can deploy your Java applications.")

[The Cloud Foundry Python Run Time](the-cloud-foundry-python-run-time-8d786ec.md "SAP Business Technology Platform provides a Cloud Foundry Python run time to which you can deploy your Python applications.")

[Multitarget Application Resource Files](../020-HANA-Cloud-DB-Dev-Get-Started/multitarget-application-resource-files-8635e0b.md "SAP HANA Cloud multitarget applications require some mandatory configuration artifacts.")

[Create the Multitarget Application Package Descriptor](create-the-multitarget-application-package-descriptor-0b0ed18.md "The package descriptor defines a JavaScript application's design-time and run-time dependencies in Cloud Foundry.")

