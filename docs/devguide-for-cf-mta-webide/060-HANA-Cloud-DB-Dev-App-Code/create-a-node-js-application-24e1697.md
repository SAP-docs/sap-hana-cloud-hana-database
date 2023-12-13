<!-- loio24e1697bdb774e52aa6f46815d539b36 -->

# Create a Node.js Application

Create a sample Node.js application.



<a name="loio24e1697bdb774e52aa6f46815d539b36__prereq_ogg_tlf_21b"/>

## Prerequisites

-   You have configured you command-line interface to use the public NPM registry. For more information, see *Related Links* below.

-   The tutorials in this section require tools provided with the CF command-line client, but you can also use graphical developer tools, for example, *SAP Web IDE Full-Stack*.




<a name="loio24e1697bdb774e52aa6f46815d539b36__steps_bg5_dpj_qv"/>

## Procedure

1.  Create a new directory named `node-tutorial`.

2.  Create a `manifest.yml` file in the `node-tutorial` directory with the following content:

    ```
    ---
    applications:
    - name: myapp
      path: myapp
    ```

    This descriptor is used to describe applications and where their sources are located.

3.  Create a new directory inside `node-tutorial` named `myapp`.

4.  Inside the `myapp` directory, create a new file called `package.json` with the following content:

    ```
    {
      "name": "myapp",
      "description": "My App",
      "version": "0.0.1",
      "dependencies": {
        "express": "4.18.2"
      },
      "scripts": {
        "start": "node start.js"
      }
    }
    ```

5.  Inside the `myapp` directory, create another file called `start.js` with the following content:

    ```
    var express = require('express');
    var app = express();
    
    app.get('/', function (req, res) {
      res.send('Hello World!');
    });
    
    var port = process.env.PORT || 3000;
    app.listen(port, function () {
      console.log('myapp listening on port ' + port);
    });
    ```

6.  To install dependencies execute the `npm install` command in the `myapp` directory.

7.  Deploy the application to the application run-time environment.

    Execute the following command in the `node-tutorial` directory.

    ```
    cf push
    ```

    You can check the state and URL of your application by using the `cf apps` command.

    > ### Output Code:  
    > ```
    > > cf apps
    > 
    > Getting apps in org <orgname> / space <spacename> as RT_ADMIN...
    > Found apps:
    > 
    > name    requested state   instances   memory    disk          urls
    > -------------------------------------------------------------------
    > myapp   STARTED           1/1         1.00 GB   <unlimited>   <URL>               
    > ```

8.  Open a browser window with your application URL.

    You should see the ***Hello World!*** message.


**Related Information**  


[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

