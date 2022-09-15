<!-- loiof1599d7974cb4511b0163c1b6ac51137 -->

# Creating the Client User Interface

Create the user interface \(GUI\) to display the database content \(HTML pages\).

The application module for the client user interface \(`web/` in the example below\) also contains the application-route description \(`xs-app.json`\), which is used by the application router module. You set up the application routes description in a subsequent step.

> ### Sample Code:  
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
> |  \- resources/                # Static resources
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
> \- mtad.yaml     
> 
> ```

