<!-- loiocaaa92b926a44bc9a5d2e6222135cb84 -->

# Application Router Extensions

Configure application-specific extensions to the application router.

An application-router extension is defined by an object with the following properties:

-   `insertMiddleware` - describes the middleware provided by this extension

    -   `first`, `beforeRequestHandler`, and `beforeErrorHandler`

        An array of middleware, where each one can be either of the following elements:

        -   A middleware function \(invoked on all requests\)

        -   An object with the following properties:

            -   `path`

                Handle requests only for this path

            -   `handler`

                The middleware function to invoke





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

The extension configuration can be referenced in the corresponding application's start script, as illustrated in the following example:

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> 
> var ar = approuter();
> ar.start({
>   extensions: [
>     require('./my-ext.js')
>   ]
> });
> ```



## Customize the Command Line

By default the application router handles its command-line parameters, but that can be customized as well.

An *<approuter\>* instance provides the property `cmdParser` that is a commander instance. It is configured with the standard, application-router, command-line options. You can add custom options like the ones illustrated in the following example:

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> 
> var ar = approuter();
> 
> var params = ar.cmdParser
>   // add here custom command line options if needed
>   .option('-d, --dummy', 'A dummy option')
>   .parse(process.argv);
> 
> console.log('Dummy option:', params.dummy);
> ```

To disable the handling of command-line options in the application router, reset the `ar.cmdParser` property to “`false`”, as illustrated in the following example:

```
ar.cmdParser = false;
```

**Related Information**  


[The Application Router Extension API](the-application-router-extension-api-c2cdc2d.md "A detailed list of the features and functions provided by the application router extension API.")

[Extend the Multitarget Application Router](extend-the-multitarget-application-router-6abdede.md "Use middleware and custom extension scripts to extend the functionalilty of the multitarget application router.")

[Custom Middleware Injection](custom-middleware-injection-ff06b76.md "Extend the application router by injecting so-called middleware plug-ins and using the “Connect” framework.")

