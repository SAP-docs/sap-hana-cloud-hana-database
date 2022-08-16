<!-- loio6abdedefcb1f47878a07d49919124eef -->

# Extend the Multitarget Application Router

Use middleware and custom extension scripts to extend the functionalilty of the multitarget application router.



## Context

There are various ways you can extend the functionality provided with the multitarget application router. You can configure JavaScript applications to use the multitarget application router as a regular Node.js package or start the multitarget application router from a dedicated script. You can inject custom middleware into the application router using predefined slots, and ensure that proper control is maintained over any injected middleware.



## Procedure

1.  Start the application router with your own JavaScript.

    Instead of starting the multitarget application router directly, you can configure your multitarget application to use its own script to start the application router, as illustrated in the following example:

    > ### Sample Code:  
    > ```
    > var approuter = require('approuter');
    > 
    > var ar = approuter();
    > ar.start();
    > ```

2.  Inject custom middleware into the multitarget application router.

    1.  Inject middleware directly in the multitarget application-router startup script.

        The multitarget application router uses the connect framework, which enables you to reuse all injected “connect” middleware within the multitarget application router, for example, directly in the application start script:

        > ### Sample Code:  
        > ```
        > var approuter = require('approuter');
        > 
        > var ar = approuter();
        > 
        > ar.beforeRequestHandler.use('/my-ext', function myMiddleware(req, res, next) {
        >   res.end('Request handled by my extension!');
        > });
        > ar.start();
        > ```

        > ### Tip:  
        > To facilitate troubleshooting, always provide a name for your custom middleware.

    2.  Add some `use` calls to middleware functions.

        The `path` argument is optional. You can also chain `use` calls, as illustrated in the following example:

        > ### Sample Code:  
        > ```
        > var approuter = require('approuter');
        > var morgan = require('morgan');
        > 
        > var ar = approuter();
        > 
        > ar.beforeRequestHandler
        >   .use(morgan('combined'))
        >   .use('/my-ext', function myMiddleware(req, res, next) {
        >     res.end('Request handled by my extension!');
        >   });
        > ar.start();
        > ```

        The multitarget application router also allows you to insert custom middleware into additional "slots": `first`, `beforeRequestHandler`, and `beforeErrorHandler`.

    3.  Return control to the application-router middleware, if necessary.

        If your middleware does not complete the request processing, call `next` to return control to the multitarget application router middleware, as illustrated in the following example:

        > ### Sample Code:  
        > ```
        > ar.beforeRequestHandler.use('/my-ext', function myMiddleware(req, res, next) {
        >   res.setHeader('x-my-ext', 'passed');
        >   next();
        > });
        > ```


3.  Configure application-specific extensions to the multitarget application router.

    You can use an extension file, for example, `my-ext.js`\) to insert middleware at the following points: `first`, `beforeRequestHandler`, and `beforeErrorHandler`.

    > ### Sample Code:  
    > Example Approuter Extension Configuration \(`my-ext.js`\)
    > 
    > ```
    > module.exports = {
    >   insertMiddleware: {
    >     first: [
    >       function logRequest(req, res, next) {
    >         console.log('Got request %s %s', req.method, req.url);
    >       }
    >     ],
    >     beforeRequestHandler: [
    >       {
    >         path: '/my-ext',
    >         handler: function myMiddleware(req, res, next) {
    >           res.end('Request handled by my extension!');
    >         }
    >       }
    >     ]
    >   }
    > };
    > ```


**Related Information**  


[Custom Middleware Injection](custom-middleware-injection-ff06b76.md "Extend the application router by injecting so-called middleware plug-ins and using the “Connect” framework.")

[Application Router Extensions](application-router-extensions-caaa92b.md "Configure application-specific extensions to the application router.")

[The Application Router Extension API](the-application-router-extension-api-c2cdc2d.md "A detailed list of the features and functions provided by the application router extension API.")

[Maintaining Multitarget Application Routes and Destinations](maintaining-multitarget-application-routes-and-destinations-0117b71.md "Define application routes and destinations.")

