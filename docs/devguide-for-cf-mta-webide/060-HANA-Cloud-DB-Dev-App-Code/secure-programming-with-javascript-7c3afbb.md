<!-- loio7c3afbb518df4df3a38ab1dda7a9417a -->

# Secure Programming with JavaScript

Web-based applications for deployment to the Cloud Foundry run-time must adhere to the general standard for Web application security as defined by the W3C.

To ensure the best possible protection against attacks, Web-based SAP HANA applications must implement not only **primary** security measures such as input validation or output encoding, but also secondary measures, for example a Content Security Policy \(CSP\) that helps defend against script-based injection vulnerabilities. In addition to any other security measures, application developers must ensure that the Web-based applications comply with the following basic rules:

-   Avoid using inline `JavaScript()` functions in a Web page.

-   Avoid using the `eval()` command.

-   Avoid using strings \(that represent code to be executed\) in place of simple functions in code generating-functions such as `setTimeout()`, `setInterval()`, or `function()`.

-   Ensure that platforms provide HTTP header-setting functions which perform the following actions:

    -   Enable CSP headers that can be maintained or customized \(for example, as a configuration option\). This is possible in either of the following ways:

        -   Indirectly

            CSP settings are derived from higher-level configurations, for example, system landscape data.

        -   Directly

            CSP settings are derived from modifications to the configuration in more simple environments.


    -   Enable applications to set CSP headers \(for example, as an API option\).


-   Make use of functions for controlling frame inclusion \(for example, frame “ancestors”\).

-   Ensure the implementation of primary protection measures such as “input validation” and “output encoding”.


> ### Note:  
> A CSP compliant application will only work if the underlying platform is also CSP compliant. For example, a CSP-compliant Web browser will not execute instructions that contradict the defined security policy.



## Recommended Coding Rules for JavaScript Applications

It is recommended to adhere to the following rules when coding JavaScript applications that are rendered by HTML in a Web browser, for example: SAPUI5-based Fiori applications, mobile applications using HTML technology, JSP applications, Web Dynpro, BSP applications, EP iViews:

-   Security policy:

    The CSP should be as close as possible to the following example:

    ```
    Content-Security-Policy: default-src 'self'; style-src 'self' 'unsafe-inline'; img-src 'self' data: 
    ```

    > ### Note:  
    > Certain adjustments might be needed to help ensure functionality, for example, adding source lists for `script-src`.

-   `<script>`

    Loading scripts from a white-listed source is allowed using the `<script>` tag, for example:

    ```
    <script src = "foo.js" type = "text/javascript" > </script >
    ```

-   `onClick()` 

    To handle events, you can set the event handler attributes of elements, or call `element.addEventListener()`, from a script that has been loaded from a white-listed site, as illustrated in the following example:

    ```
    element.onclick = someFunction; 
    element. addEventListener( "click" , someFunction, false ) ; 
    ```

-   `setInterval()` 

    ```
    window. setInterval( myFunc, 10000 ) ;
    ```

-   `setTimeout()` 

    ```
    self.timers.invite2xxTimer = window.setTimeout(function() {invite2xxRetransmission(retransmissions)}, timeout); 
    ```




## Coding Practices to Avoid in JavaScript Applications

It is recommended to avoid the following commonly used practices when coding Web-based JavaScript applications for SAP HANA:

-   `<script>`

    Avoid including any executable code in an HTML string:

    ```
    <script type = "text/javascript" > /* executable code */ </script >
    ```

-   `onClick()` 

    Avoid including any executable code in an HTML string:

    ```
    <a onclick = "another_evil_script()"  > Click this for some awesome fun! </a >  
    ```

    Avoid specifying a JavaScript command as part of an HTML attribute; this is forbidden by the CSP policy:

    ```
    <a href = "javascript:do_something_evil()" > Click here for some awesome fun! </a >
    ```

-   `setInterval()` 

    Avoid including any executable code in an HTML string:

    ```
    window. setInterval(  "evil_code()" , 10000 ) ;
    ```

-   `setTimeout()` 

    In the following short example, if “`invite2xxRetransmission`” returns a string instead of a pointer, it will be still evaluated using the `eval()`function:

    ```
    self.timers.invite2xxTimer =  window.setTimeout(invite2xxRetransmission(retransmissions), timeout); 
    ```




<a name="loio7c3afbb518df4df3a38ab1dda7a9417a__section_b13_dbd_cnb"/>

## SSL Setup with Node.js Applications

SAP provides the package \(`@sap/hdbext`\) which Node.js applications can use to connect to SAP HANA Cloud. If you want to use it, you must add it to your list of application dependencies.

> ### Tip:  
> To ensure that both SSL and trust certificates are set up automatically, it is recommended to use [@sap/hdbext](https://www.npmjs.com/package/@sap/hdbext) to connect to SAP HANA rather than use @sap/hana-client. For more details about connections to SAP HANA, see *Related Information* below.

**Related Information**  


[Getting Started with Multitarget Application Development in Cloud Foundry on SAP BTP](../020-HANA-Cloud-DB-Dev-Get-Started/getting-started-with-multitarget-application-development-in-cloud-foundry-on-sa-7f681c3.md "Multitarget applications running in Cloud Foundry on SAP Business Technology Platform (SAP BTP) must include a number of mandatory files that are used for configuration and deployment.")

[The Cloud Foundry JavaScript Run Time](the-cloud-foundry-javascript-run-time-18c0192.md "Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.")

[https://www.npmjs.com/package/@sap/hana-client](https://www.npmjs.com/package/@sap/hana-client)

[Connect to SAP HANA Cloud](connect-to-sap-hana-cloud-31d5595.md "Connect an application to SAP HANA Cloud")

