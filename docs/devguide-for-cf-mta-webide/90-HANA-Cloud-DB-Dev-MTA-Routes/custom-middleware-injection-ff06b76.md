<!-- loioff06b76b66bb46a985bcd495c6269611 -->

# Custom Middleware Injection

Extend the application router by injecting so-called middleware plug-ins and using the “Connect” framework.

The application router uses the connect framework, for more information, see *Connect framework* in the *Related Links* below. You can reuse all injected “connect” middleware within the application router, for example, directly in the application start script:

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

The `path` argument is optional. You can also chain `use` calls.

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

The application router defines the following slots where you can insert custom middleware:

-   `first` - right after the connect application is created, and before any application router middleware. At this point security checks are not performed yet.

    > ### Tip:  
    > This is good place for infrastructure logic, for example, logging and monitoring.

-   `beforeRequestHandler` - before standard application router request handling, that is static resource serving or forwarding to destinations.

    > ### Tip:  
    > This is a good place to handle custom REST API requests.

-   `beforeErrorHandler` - before standard application router error handling.

    > ### Tip:  
    > This is a good place to capture or customize error handling.


If your middleware does not complete the request processing, call `next` to return control to the application router middleware, as illustrated in the following example:

> ### Sample Code:  
> ```
> ar.beforeRequestHandler.use('/my-ext', function myMiddleware(req, res, next) {
>   res.setHeader('x-my-ext', 'passed');
>   next();
> });
> ```

**Related Information**  


[Middleware Connect Framework](https://github.com/senchalabs/connect)

[Extend the Multitarget Application Router](extend-the-multitarget-application-router-6abdede.md "Use middleware and custom extension scripts to extend the functionalilty of the multitarget application router.")

[Application Router Extensions](application-router-extensions-caaa92b.md "Configure application-specific extensions to the application router.")

[The Application Router Extension API](the-application-router-extension-api-c2cdc2d.md "A detailed list of the features and functions provided by the application router extension API.")

