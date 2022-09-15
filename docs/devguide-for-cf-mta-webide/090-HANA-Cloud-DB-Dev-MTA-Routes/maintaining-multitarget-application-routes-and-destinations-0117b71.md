<!-- loio0117b71251314272bfe904a2600e89c0 -->

# Maintaining Multitarget Application Routes and Destinations

Define application routes and destinations.

In Cloud Foundry the application router \(“approuter”\) is the entry point for a multitarget business application and is used for routing incoming requests to the appropriate microservices. The application routes are defined in the application descriptor `xs-app.json`, a JSON-formatted file that is mandatory for the approuter. In the following example, the approuter is located in the `web/` directory, so the `xs-app.json` application descriptor must be placed there, too.

> ### Sample Code:  
> Application Routes Configuration
> 
> ```
> JavaScript-AppName
> |- db/                        
> |  |- package.json            
> |  |- src/                    
> |     |- .hdiconfig           
> |     \- mytable.hdbdd        
> |- web/                         # Application descriptors
> |  |- xs-app.json               # Application routes configuration
> |  |- package.json              # Application router details/dependencies
> |  \- resources/              
> |- js/                        
> |  |- start.js                
> |  |- package.json            
> |  \- src/                    
> |     \- odata/               
> |        |- resources/        
> |        \- services/         
> |           | - srv1.xsodata  
> |           \ - srvN.xsodata  
> |- security/                  
> |  \- xs-security.json        
> |- manifest.yml
> \- mtad.yaml     
> 
> ```

**Related Information**  


[Configure the Multitarget Application Router](configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

[Application-Router Resource Files](application-router-resource-files-8dccaad.md "The routing configuration for an application is defined in one or more so-called &quot;destinations&quot; that are defined in a destinations configuration.")

