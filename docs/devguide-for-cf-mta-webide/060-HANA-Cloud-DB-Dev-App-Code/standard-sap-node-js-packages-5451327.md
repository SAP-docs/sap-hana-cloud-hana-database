<!-- loio54513272339246049bf438a03a8095e4 -->

# Standard SAP Node.js Packages

A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.



SAP provides a selection of standard Node.js packages, which are available for download and use from the NPM public registry at [https://registry.npmjs.org](https://registry.npmjs.org). For more information about the NPM public registry as well as how to configure your multitarget application to use the registry, see *The NPM Registry* in *Related Information* below.

The following table lists the SAP Node.js packages that are currently available and indicates where you can find them. For more details about the contents of each Node.js packages as well as any configuration tips, see the `README` file in the corresponding NPM package.

> ### Note:  
> Some packages are available for download but are neither listed nor documented here, for example, packages that are included in the registry only because they are required by other packages.

**SAP Node.js Packages and Contents**


<table>
<tr>
<th valign="top">

Package Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [`@sap/audit-logging`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_cgq_w5l_mv) 



</td>
<td valign="top">

Utilities for audit logging



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/approuter`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_zrn_flt_vt) 



</td>
<td valign="top">

The application router is the single entry point for the \(business\) application. It serves static content, authenticates users, rewrites URLs, and routes requests to other micro services as well as propagating user information.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/cds`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_mz5_bqq_25) \*



</td>
<td valign="top">

Core Data Services \(CDS\) client for SAP CAP

> ### Note:  
> The `@sap/cds` library version < 1.15.x is intended for use with XS advanced \(on-premise\) and cannot be used in SAP HANA Cloud scenarios, since the `hdbcds` artifact type is not supported. Versions 2.x.x and 3.x.x of the library `@sap/cds` are only for use in SAP Cloud Application Programming Model \(CAP CD+S\) scenarios.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/dwf-deploy`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_qps_rvm_cz) 



</td>
<td valign="top">

Node.js client for SAP HANA Data Warehousing Foundation 2.0 \(HANA DWF 2.0\) to deploy design-time artifacts



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/dwf-generator`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_tkt_x1s_k1b) 



</td>
<td valign="top">

Node.js client for SAP HANA Data Warehousing Foundation 2.0 \(HANA DWF 2.0\) to generate design-time artifacts



</td>
</tr>
<tr>
<td valign="top">

[`@sap/dwf-dws-client`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_ic3_fds_k1b)



</td>
<td valign="top">

Node.js client for SAP HANA Data Warehousing Foundation 2.0 \(HANA DWF 2.0\) to host task types for the Task Orchestration Engine



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/e2e-trace`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_atm_w5l_mv) 



</td>
<td valign="top">

Utilities for end-to-end tracing \(in particular the handling of SAP Passports\)



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/edmx2csn`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_lrt_rys_pgb) 



</td>
<td valign="top">

A utility to convert an OData V2 model \(EDMX\) to Core Schema Notation \(CSN\)



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/hdb-connection`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_rmz_bqq_25) 



</td>
<td valign="top">

Utility functions for access to SAP HANA in Node.js

> ### Note:  
> The functions included in the `@sap/hdb-connection` library have been superseded; use `@sap/hdbext` instead.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/hdbext`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_ilt_mkt_vt) 



</td>
<td valign="top">

Extends the functionality of the `@sap/hana-client` package.

> ### Note:  
> The functionality included in the `@sap/hdbext` library replaces and supersedes the functions previously provided by the `@sap/hdb-connection` library.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/hana-client`](https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.02/en-US/a5c332936d9f47d8b820a4ecc427352c.html) 



</td>
<td valign="top">

A client library for communication with the SAP HANA database.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/hdi-deploy`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_lbd_jwf_k5) 



</td>
<td valign="top">

The Node.js based “HDI deploy” application \(also known as “DeployApp”\) which is based on HDI's SQL interface



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/hdi-dynamic-deploy`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_rww_bfp_tcb) 



</td>
<td valign="top">

A Node.js-based HTTP server for the deployment of database content to dynamically created SAP HANA DI \(HDI\) containers



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/hdi`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_k3r_2wm_cz) 



</td>
<td valign="top">

A Node.js-based client library for SAP HANA DI \(HDI\)



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/jobs-client`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_xvk_f3t_vt) 



</td>
<td valign="top">

A client library for the Job Scheduler service.



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/logging`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_vwt_l3t_vt) 



</td>
<td valign="top">

Provides logging and tracing functions for Node.js applications. Logs and traces are written in the standard SAP format and in the appropriate JSON format in CloudFoundry \(from version ^4.0.0\).



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/node-vsi`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_wxk_pqk_xz) 



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/sds-deploy`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_mn4_w5l_mv) 



</td>
<td valign="top">

Node.js client for the SAP HANA Streaming Analytics option



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/site-entry`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_lk1_dtq_sy) 



</td>
<td valign="top">

SAP Portal site entry point



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/site-content-deployer`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_pth_dtq_sy) 



</td>
<td valign="top">

Client for portal site content deployer



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/site-app-server`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_hs2_fpt_2z) 



</td>
<td valign="top">

An application server for the independent apps scenario on the SAP portalA Node.js client that contains the Virus Scanning Interface \(VSI\) binding for Node.js



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xsenv`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_yqn_r4t_vt) 



</td>
<td valign="top">

Utility for easy setup and access of Cloud Foundry environment variables and services



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xsjs`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_dwh_dpt_vt) 



</td>
<td valign="top">

A Node.js client that contains the Virus Scanning Interface \(VSI\)Compatibility layer for SAP HANA extended application services, classic model \(SAP HANA XS Classic\) applications to run on JavaScript run time in SAP HANA extended application services, advanced model \(SAP HANA XS Advanced\).



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xsjs-test`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_bhp_hsl_mv) 



</td>
<td valign="top">

Unit test framework for the compatibility layer \(XS classic runtime\)



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xssec`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_atx_2vt_vt) 



</td>
<td valign="top">

Security API for Node.js, including the HDI container security API for Node.js



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xss-secure`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_mvj_4kt_vt) 



</td>
<td valign="top">

Utilities for protection against cross-site scripting



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xb-msg`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_p4f_zxd_sy) 



</td>
<td valign="top">

Provides messaging capabilities with a message broker



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xb-msg-env`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_tv5_wkj_tgb) 



</td>
<td valign="top">

Provides the functions needed to set up messaging client options from Cloud Foundry environment variables



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xb-msg-amqp-v091`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_fcw_zxd_sy) 



</td>
<td valign="top">

Provides a client implementation for AMQP v0.9.1



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xb-msg-amqp-v100`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_ox3_nlr_pgb) 



</td>
<td valign="top">

Provides a client implementation for AMQP v100



</td>
</tr>
<tr>
<td valign="top">

 [`@sap/xb-msg-mqtt-v311`](standard-sap-node-js-packages-5451327.md#loio54513272339246049bf438a03a8095e4__section_fy2_yxd_sy) 



</td>
<td valign="top">

Provides a client implementation for MQTT v3.1.1



</td>
</tr>
</table>



<a name="loio54513272339246049bf438a03a8095e4__section_zrn_flt_vt"/>

## @sap/approuter

The application router is the single entry point for the \(business\) application. The main tasks of the application router are to serve static content, authenticate users, rewrite URLs, and proxy requests to other micro services while propagating user information. For more information about the Node.js application router and how to configure it for your application, see the section *Maintaining Multitarget Application Routes and Destinations* in this guide or the *Related Links* section below.



<a name="loio54513272339246049bf438a03a8095e4__section_mz5_bqq_25"/>

## @sap/cds

The Core Data Services for Node.js \(`@sap/cds`\) comprise a JavaScript client library for Core Data Services that enable Node.js applications to consume CDS artifacts natively in Node.js applications.



### Usage

> ### Sample Code:  
> ```
> var cds = require('@sap/cds'); 
> ```

CDS entities are imported by name. The import function takes a callback that is invoked when all imports have completed. Additional fields and overrides can be supplied for each entity.

> ### Note:  
> The import operation is a regular asynchronous Node.js function; you can import entities at any point in time, and in as many calls as you want.

> ### Sample Code:  
> ```
> cds.importEntities([
>     { $entity: "xsds.test.cds::ds_test.e1" },
>     { $entity: "xsds.test.cds::ds_test.e2",
>       $fields: {
>           a: { $association: "xsds.test.cds::ds_test.e2",
>                $viaBacklink: "b" }
>       }
>     }
> ], callback);
> 
> function callback(error, entities) {
>     var E1 = entities["xsds.test.cds::ds_test.e1"];
>     var E2 = entities["xsds.test.cds::ds_test.e2"];
>     // ...
> }
> 
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_qps_rvm_cz"/>

## @sap/dwf-deploy

This package includes a Node.js client for SAP HANA Datawarehousing Foundation \(HANA DWF\). The following table describes the file-system layout required by the `HANA DWF Client` application:

**HANA DWF Client File System Layout**


<table>
<tr>
<th valign="top">

File



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `package.json` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Used by the Node.js package manager \(`npm`\) to boot and start the application.



</td>
</tr>
<tr>
<td valign="top">

 `src/` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Subdirectory containing `DWF` deployment definition files \(optional, additional subfolders are allowed\).



</td>
</tr>
<tr>
<td valign="top">

 `cfg/` 



</td>
<td valign="top">

No



</td>
<td valign="top">

Additional deployment subdirectories ...



</td>
</tr>
</table>

> ### Note:  
> All DWF-related files in the **root** directory are ignored by the `HANA DWF Client` application.



<a name="loio54513272339246049bf438a03a8095e4__section_tkt_x1s_k1b"/>

## @sap/dwf-generator

This package includes a Node.js client for SAP HANA Datawarehousing Foundation 2.0 \(HANA DWF 2.0\) to generate designtime artifacts. The following table describes the file-system layout required by the`HANA DWF Client` application:

**HANA DWF Client File System Layout**


<table>
<tr>
<th valign="top">

File



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `package.json` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Used by the `dwf-generator` to discover the `dwf-config`.



</td>
</tr>
<tr>
<td valign="top">

 `src/` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Subdirectory containing `DWF` deployment definition files \(optional, additional subfolders are allowed\).



</td>
</tr>
<tr>
<td valign="top">

 `src/dlm_generated` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Subdirectory containing `XSA` or `DWF` deployment definition files \(optional, additional subfolders are allowed\).



</td>
</tr>
<tr>
<td valign="top">

 `cfg/` 



</td>
<td valign="top">

No



</td>
<td valign="top">

Additional deployment subdirectories, which are created in the designtime



</td>
</tr>
<tr>
<td valign="top">

 `cfg/dlm_generated` 



</td>
<td valign="top">

No



</td>
<td valign="top">

Additional deployment subdirectories, which are generated, based on the deployment definition files that have been created in the designtime.



</td>
</tr>
</table>

> ### Note:  
> All DWF-related files in the **root** directory are ignored by the `HANA DWF Client` application.



<a name="loio54513272339246049bf438a03a8095e4__section_ic3_fds_k1b"/>

## @sap/dwf-dws-client

This package includes a Node.js client for SAP HANA Datawarehousing Foundation 2.0 \(HANA DWF 2.0\) to host task types for the `Task Orchestration Engine`. The module does not imply any requirements to the file system structure.



<a name="loio54513272339246049bf438a03a8095e4__section_lrt_rys_pgb"/>

## @sap/edmx2csn

The `EDMX2CSN` utility converts an OData V2 model \(EDMX\) into Core Schema Notation \(CSN\), which is a JSON-like format that enable the compact representation of data and service models. This utility is primarily intended for developers who are building an extension application that connects to a remote OData V2 data source such as SAP S/4HANA. In such a case, converting the EDMX model from the OData V2 data source into CSN is the first step you take, along with building the CDS data model, in the process of defining the CDS service model for your application.



### Usage

The compiler with its options is invoked like any other `npm` or Unix command:

-   To generate a CSN file from an EDMX **file**, use the following command:

    -   Windows \(`edmx2csn.cmd`\):

        ```
        $homedir>./node_modules/.bin/edmx2csn.cmd -i ${input_folder}/metadata.xml -o ${output_folder} -f
        ```

    -   Linux: \(`edmx2csn.sh`\):

        ```
        $homedir>./node_modules/.bin/edmx2csn.sh -i ${input_folder}/metadata.xml -o ${output_folder} -f
        ```


-   To generate a CSN file from an EDMX **URL**, use the following command:

    -   Windows \(`edmx2csn.cmd`\):

        ```
        $homedir>./node_modules/.bin/edmx2csn.cmd -i ${service_url}/$metadata -o ${output_folder}
        ```

    -   Linux: \(`edmx2csn.sh`\):

        ```
        $homedir>./node_modules/.bin/edmx2csn.sh -i ${service_url}/$metadata -o ${output_folder}
        ```



The following table provides details of the options used in the examples of the `edmx2csn` command above:


<table>
<tr>
<th valign="top">

Option



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

*\-i*



</td>
<td valign="top">

Specifies the name and location of the OData model to be converted to CSN \(using either a file path or the URL of a service metadata end point\)



</td>
</tr>
<tr>
<td valign="top">

*\-o*



</td>
<td valign="top">

Specifies the location of the CSN file produced by the conversion process



</td>
</tr>
<tr>
<td valign="top">

*\-f*



</td>
<td valign="top">

Overwrite an existing CSN output file



</td>
</tr>
</table>



<a name="loio54513272339246049bf438a03a8095e4__section_rmz_bqq_25"/>

## @sap/hdb-connection

This package comprises a small library that enables you to establish a connection to an SAP HANA server using the credentials either from stand-alone environments or, if required, from a Cloud Foundry environment, for example defined in the “`VCAP_SERVICES`” environment variables.

> ### Restriction:  
> The functions included in the `@sap/hdb-connection` library have been superseded; use `@sap/hdbext` instead.



<a name="loio54513272339246049bf438a03a8095e4__section_ilt_mkt_vt"/>

## @sap/hdbext

This is a small Node.js package that extends the functionality of the `@sap/hana-client` package. The functionality included in the `@sap/hdbext` library replaces and supersedes the functions previously provided by the `@sap/hdb-connection` library.

> ### Tip:  
> To ensure that both SSL and trust certificates are set up automatically, it is recommended to use [@sap/hdbext](https://www.npmjs.com/package/@sap/hdbext) to connect to SAP HANA rather than use @sap/hana-client.



### Usage

> ### Sample Code:  
> ```
> var hdbext = require('@sap/hdbext'); 
> ```

The following code example shows how to create a connection to the SAP HANA database:

> ### Sample Code:  
> ```
> var hanaConfig = { 
>   host : 'hostname', 
>   port : 30015, 
>   user : 'user', 
>   password : 'secret' 
> }; 
> hdbext.createConnection(hanaConfig, function(error, client) { 
>   if (error) { 
>     return console.error(error); 
>   } 
>   client.exec(...); 
> }); 
> ```

If you are using table parameters,with the new API you can pass an array of objects and it will auto convert it into a table parameter, as illustrated in the following example:

> ### Sample Code:  
> ```
> create procedure PROC_DUMMY (in a int, in b int, out c int, out d DUMMY, out e TABLES)
>   language sqlscript 
>   reads sql data as 
>   begin 
>     c := :a + :b; 
>     d = select * from DUMMY; 
>     e = select * from TABLES; 
>   end 
> ```

With the `loadProcedure()` API, you can make the following call:

> ### Sample Code:  
> ```
> hdbext.loadProcedure(client, 'MY_SCHEMA', 'PROC_DUMMY', function(err, sp) { 
>   sp({ A: 3, B: 4 }, function(err, parameters, dummyRows, tableRows) { 
>     if (err) { 
>       return console.error(err); 
>     } 
> 
>     console.log('C:', parameters.C); 
>     console.log('Dummies:', dummyRows); 
>     console.log('Tables:', tableRows);
>   }); 
> }); 
> ```

To use connection pooling, specify the property `pooling` with value of `true` \(JavaScript boolean\) in the `hanaConfig` object.

To acquire a client from the connection pool, use the `pool.acquire` function, as illustrated below:

> ### Sample Code:  
> ```
> pool.acquire(options, function(err, client) {});
> ```

> ### Note:  
> Use the `options` object if you need to change the settings configured for the pooled connection.

If the client is no longer needed, release it to the connection pool, as illustrated in the following example:

> ### Sample Code:  
> ```
> pool.release(client);
> ```

Alternatively, you can close the client connection, as illustrated below:

> ### Sample Code:  
> ```
> client.close();
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_lbd_jwf_k5"/>

## @sap/hdi-deploy

`@sap/hdi-deploy` is the Node.js deploy application \(known as “`DeployApp`”\) for the SAP HANA Deployment Infrastructure \(HDI\), which is based on the HDI's SQL interface. The following table describes the file-system layout required by the `DeployApp` application:

**HI Deployer File System Layout**


<table>
<tr>
<th valign="top">

File



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `package.json` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Used by the Node.js package manager \(`npm` 



</td>
</tr>
<tr>
<td valign="top">

 `src/` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Subdirectory containing `.hdiconfig` and HDI deployment definition files \(optional, additional subfolders are allowed\).



</td>
</tr>
<tr>
<td valign="top">

 `cfg/` 



</td>
<td valign="top">

No



</td>
<td valign="top">

Additional deployment subdirectories ...



</td>
</tr>
</table>

> ### Note:  
> All HDI-related files in the **root** directory are ignored by the `DeployApp` application.

For more information about setting up and using the Node.js-based SAP HANA Deployment Infrastructure \(HDI\) Deployer, see *Configuring the HDI Deployer* in the *Related Links* below.



### Environment Variables

The following table lists the environment variables that can be used with the \) to boot and start the application.`DeployApp` application:

**HDI Deployer Environment Variables for Multitarget Applications**


<table>
<tr>
<th valign="top">

Variable



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `TARGET_CONTAINER` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

\) toService name that specifies the HDI target container \(required if more than one service is bound to the `DeployApp` application\).



</td>
</tr>
<tr>
<td valign="top">

 `SERVICE_REPLACEMENTS` 



</td>
<td valign="top">

No



</td>
<td valign="top">

JSON-structured list of service replacements,

```
[ 
  { 
   "key": "logical-service-name-1", 
   "service":"real-service-name-1"
  }, 
  { 
   "key": "logical-service-name-2", 
   "service":"real-service-name-2"
  }
]
```

The **logical** service names refer to the names in the HDI content; the **real** service names refer to the services which are bound to the HDI Deployer via `VCAP_SERVICES`. If the HDI content references a service name which is not listed in the replacements, this name is used as a real service name.



</td>
</tr>
</table>

The structure of the *<SERVICE\_REPLACEMENTS\>* environment variable illustrated in the following example is intended to enable and facilitate MTA group assignments.

> ### Code Syntax:  
> Service Replacements list in the `manifest.yml` file
> 
> ```
> applications: 
> - name: app-db 
>   path: db 
>   services: 
>     - app-database 
>     - real-grantor-service 
>     - real-external-service 
>   env: 
>     TARGET_CONTAINER: app-database 
>     SERVICE_REPLACEMENTS:  
>     [
>       { 
>         "key" : "logical-grantor-service", 
>         "service" : "real-grantor-service"
>       },
>       { 
>         "key" : "logical-external-service", 
>         "service" : "real-external-service"
>       }
>     ] 
> ```



### Removing Deployed SAP HANA Node.js Artifacts

The `DeployApp` deletes \(recursively\) all artifacts found in the folder `src/` \(and `cfg/`, if the optional subfolder exists\) before the deployment of changed or new artifacts, but deleted artifacts are not removed; they remain deployed. To remove deployed artifacts, you have the following options:

-   Specify the deployed files to remove in an `undeploy.json` file placed in the root directory of the deployment artifacts; the file lists the paths to and the name of the artifacts to remove:

    > ### Sample Code:  
    > ```
    > [
    >   "src/AddressBook.hdbtable",
    >   "src/AddressBookView.hdbview"
    > ]
    > ```

-   Start the `DeployApp` with the `--autoUndeploy` option

    `node deploy --autoUndeploy`




<a name="loio54513272339246049bf438a03a8095e4__section_rww_bfp_tcb"/>

## @sap/hdi-dynamic-deploy

This module provides a Node.js-based HTTP server that can be used to deploy database content to dynamically created HDI containers, for example, containers created by means of the Instance Manager. `@sap/hdi-dynamic-deploy` is based on `@sap/hdi-deploy` which should be used if a static deployment at deployment time is sufficient.



### Usage

Typically, `@sap/hdi-dynamic-deploy` is installed by including a dependency in the `package.json` file of your multitarget application's database module, as illustrated in the following example:

> ### Sample Code:  
> `myApp/db/package.json`
> 
> ```
> {
>   "name": "deploy",
>   "dependencies": { 
>      "@sap/hdi-dynamic-deploy": "1.1.0" 
>   }, 
>   "scripts": { 
>      "start": "node node_modules/@sap/hdi-dynamic-deploy/"
>   }
> } 
> ```

For more detailed information about using the `@sap/hdi-dynamic-deploy`, see the `README.md` file included in the NPM package.



### Configuration

Before using the HDI Dynamic Deployer, you must configure the following connection-related environment variables:

-   `PORT`

    The port the HTTP server listens on

-   `hdi_dynamic_deploy_user`

    The user name to supply for HTTP-based basic authentication

-   `hdi_dynamic_deploy_password`

    The password to use for HTTP-based basic authentication


The `PORT` variable is set automatically; both the user name and password must be defined in the multitarget application's development descriptor, `mta.yaml`, as illustrated in the following example:

> ### Code Syntax:  
> HDI Dynamic Deployer Configuration in `mta.yaml`
> 
> ```
> modules: 
>   - name: db  
>     type: com.sap.xs.hdi-dynamic  
>     path: db  
>     properties:  
>       hdi_dynamic_deploy_user: ${generated-user}  
>       hdi_dynamic_deploy_password: ${generated-password}  
>     provides:
>     - name: db_deployment 
>       properties: 
>          url: ${default-url} 
>          user: ${generated-user} 
>          password: ${generated-password} 
> ```



### Multi-Tenancy Scenarios

A multi-target application \(MTA\) for use in multi-tenancy scenarios typically includes multiple database modules:

-   N static database modules \(`type: com.sap.xs.hdi`\),

    For configuration or shared data. A static module depends on `@sap/hdi-deploy`; it does not depend on `@sap/hdi-dynamic-deploy`.

-   M dynamic database modules \(`type: com.sap.xs.hdi-dynamic`\)

    Which contain the business data for a certain type of tenant. A dynamic module depends on `@sap/hdi-dynamic-deploy`, which internally depends on `@sap/hdi-deploy` for deployment to the correct tenant.


> ### Code Syntax:  
> Dynamic Deployment in a Multi-Tenancy Scenario
> 
> ```
> modules:
>   - name: db-static-1 
>   - type: com.sap.xs.hdi 
>   - path: db-static-1 
> 
>   - name: db-static-2
>     type: com.sap.xs.hdi 
>     path: db-static-2 
> 
>   - name: db-dynamic-1 
>     type: com.sap.xs.hdi-dynamic 
>     path: db-dynamic-1 
> 
>   - name: db-dynamic-2 
>     type: com.sap.xs.hdi-dynamic 
>     path: db-dynamic-2 
> 
>   - name: db-dynamic-3 
>     type: com.sap.xs.hdi-dynamic 
>     path: db-dynamic-3 
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_k3r_2wm_cz"/>

## @sap/hdi

This module provides a Node.js-based client library for SAP HANA DI \(HDI\). The client library provides the following asynchronous methods to enable access to HDI functionality:

-   `connect`

-   `disconnect`

-   `configureDI`

    > ### Caution:  
    > Deprecated; use `configureDIParameters` instead.

-   `configureDIParameters`

-   `createContainer`

-   `dropContainer`

-   `configureContainer`

    > ### Caution:  
    > Deprecated; use `configureContainerParameters` instead.

-   `configureContainerParameters`

-   `listLibraries`

-   `configureLibraries`

-   `listConfiguredLibraries`

-   `status`

-   `read`

-   `listDeployed`

    Read object-related metadata.

-   `readDeployed`

    Read object-related metadata **and** its content.

-   `write`

-   `delete`

-   `make`

-   `makeAsync`

-   `grantContainerApiPrivileges`

-   `grantContainerApiPrivilegesWithGrantOption`

-   `revokeContainerApiPrivileges`

-   `grantContainerSchemaPrivileges`

-   `revokeContainerSchemaPrivileges`

-   `grantContainerSchemaRoles`

-   `revokeContainerSchemaRoles` 




### Overview

After installing the module using `npm`, an application must create an instance of the client, for example:

```
hdi = new HDI(container, logger, credentials);
```

In this example:

-   “`container`”

    The name of an existing HDI container

-   “`logger`”

    A callback function used to write logging information

-   “`credentials`”

    An object containing the host name, port, user, and password that are used to establish the connection to the database, for example:

    ```
    { host : '<myhost.kumasi.acme.com>', 
      port : 30015, 
      user : 'Kwame', 
      password : 'etisei!131'} 
    ```


The connection to the database is established with the `connect()` method, which takes only a callback function as parameter. When the application console.log\(instance\); instanceManager.delete\('my-tenant', function \(err\) \{ if \(err\) \{ return console.log\('Delete error:', err.message\); \} console.log\('Instance deleted'\); \}\); \}\); \}\); \}\);

```
hdi.disconnect();
```



<a name="loio54513272339246049bf438a03a8095e4__section_xvk_f3t_vt"/>

## @sap/jobs-client

`@sap/jobs-client` is a small Node.js package to integrate jobs into your Node.js application. The package contains utilities that enable you to create REST calls conforming to the format expected by the SAP HANA job scheduler service, which is used to register or unregister jobs, update job schedules, and display the job status.

This package works with job descriptor objects and uses properties defined according to the requirements of the corresponding service in Job Scheduler.



### Usage

> ### Sample Code:  
> ```
> var jobsc = require('@sap/jobs-client'); 
> 
> var options = { 
>   host: 'localhost', 
>   port: 4242, 
>   timeout: 15000, 
>   user: 'username', 
>   password: 'password', 
>   baseURL: 'http://apphost:port/' 
> }; 
> 
> var myJob = { /* according to job scheduler documentation */ }; 
> 
> var scheduler = new jobsc.Scheduler(options); 
> var scJob = { job: myJob }; 
> 
> scheduler.createJob(scJob, function (error, body) { 
>   if (error) { 
>     return console.log('Error registering new job %s', error);
>   } 
>   // job was created successfully job.id = body._id;
> }); 
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_vwt_l3t_vt"/>

## @sap/logging

Provides logging and tracing functions for Node.js applications; logs and traces are written using the standard JSON format in Cloud Foundry \(from version ^4.0.0\).



### Usage

> ### Sample Code:  
> ```
> var logging = require('@sap/logging');
> var express = require('express');
> 
> var app = express();
> 
> var appContext = logging.createAppContext();
> 
> app.use(logging.middleware({ appContext: appContext, logNetwork: true })); and provides the single API
> 				function: var logging = require('@sap/logging');
> var express = require('express');
> 
> var app = express();
> 
> var appContext = logging.createAppContext();
> 
> app.use(logging.middleware({ appContext: appContext, logNetwork: true }));
> 
> app.get('/demo', function (req, res) {
>   var logger = req.loggingContext.getLogger('/Application/Network');
>   var tracer = req.loggingContext.getTracer(__filename);
> 
>   logger.info('Retrieving demo greeting ...');
> 
> app.get('/demo', function (req, res) {
>   var logger = req.loggingContext.getLogger('/Application/Network');
>   var tracer = req.loggingContext.getTracer(__filename);
> 
>   logger.info('Retrieving demo greeting ...');
>   tracer.info('Processing GET request to /demo');
> 
>   res.send('Hello World!');
> });
> 
> app.listen(3000, function() {
>   console.log('Server started');
> });
> ```

You need to perform the following actions:

1.  Create the application context by initializing the logging library with some application-wide options.

2.  Specify the middleware to use to extract information about a specific request. The specified middleware is used to extract request-specific information and attach the `loggingContext` property to the request object.

    > ### Note:  
    > This middleware definition should come **before** the `request-user` is set.

3.  Instantiate a logger and a tracer by using the `loggingContext` property of the request.

4.  Log and trace whatever you need.




### Severity Levels

The following severity levels can be used in logging and tracing:

-   Logging:

    “**info**” \(default\), “warning”, “error”, and “fatal”

-   Tracing:

    “debug”, “path”, “info”, “warning”, “**error**” \(default\), and “fatal”


It is possible to set a maximum priority level for all loggers and tracers by using the environment variable `XS_APP_LOG_LEVEL`. Its value is a level from “`debug`” to “`fatal`”. The value from the environment variable \(if valid\) will be used instead of all already set levels. This is especially suitable for debugging purposes.

> ### Note:  
> If `XS_APP_LOG_LEVEL = none`, all logging and tracing is disabled. This setting is useful for automated testing.



### Using Loggers

The following example shows how to create a logger:

> ### Sample Code:  
> ```
> var logger = req.loggingContext.getLogger('/Application/Network');
> ```

The request context has the “`getLogger`” function that takes a single string argument; namely, the “category”. Categories define the names of functional areas in an application. It is recommended to prefix the name of your categories with “`/Application`”, for example, `/Application/Network`. The categories form a hierarchy with forward slash as the separator. The following code shows how to use the `getLevel()` command to retrieve the severity level \(as a string\) of a logger:

> ### Sample Code:  
> ```
> var level = logger.getLevel();
> ```

It is also possible to check whether an entry with a specific severity level will be logged with the current level configuration:

> ### Sample Code:  
> ```
> var willItBeLogged = logger.isEnabled('info');
> ```

The following logging entries are available: “`info`”, “`warning`”, “`error`”, and “`fatal`”.

> ### Sample Code:  
> ```
> logger.info('Successful login of user %s - ', user, new Date());
> logger.warning('Job did not complete successfully. An app admin must retrigger the job.');
> logger.error(new Error('Sorry! An error occurred'));
> logger.fatal('A fatal error has occurred; the application has stopped!');
> ```



### Using Tracers

To obtain a tracer, use the `getTracer()` command, as illustrated in the following example:

> ### Sample Code:  
> ```
> var tracer = req.loggingContext.getTracer(__filename);
> ```

In the same way as with loggers, you can also retrieve and check tracer instances, as illustrated in the following example:

> ### Sample Code:  
> ```
> var level = tracer.getLevel();
> var willItBeTraced = tracer.isEnabled('path');
> // etc.
> ```

The tracing API provides the following methods to enable you to set up and use tracing in Node.js applications:

-   Entering

    Record that a function has been entered in the program flow. You can pass all of the arguments of your function to the entering function so that they are traced.

-   Exiting

    Typically used in combination with the “entering” method. If you provide an argument, it will be considered as the return value of your function.

-   Throwing

    Used to trace when the code is about to throw an error; you can pass the error that is about to be thrown as an argument.

-   Catching

    Used in catch blocks; you can pass the caught error as an argument.


> ### Sample Code:  
> Tracing Methods: Entering and Exiting
> 
> ```
> function myFunction(tracer, a, b ,c) {
>   tracer.entering(a, b, c);
> 
>   var result = // some logic here ...
> 
>   tracer.exiting(result);
>   return result;
> }
> ```

> ### Sample Code:  
> Tracing Methods: Throwing and Catching
> 
> ```
> function func1(tracer) {
>   var error = new Error('An error has occurred');
>   tracer.throwing(error);
>   throw err;
> }
> 
> function func2(tracer) {
>   try {
>     func1(tracer);
>   } catch (err) {
>     tracer.catching(err);
>     // logic for processing the error
>   }
> }
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_yqn_r4t_vt"/>

## @sap/xsenv

This is a small Node.js package to enable easy setup of \(and access to\) environment variables and services in Cloud Foundry.



### Usage

The following example shows you how to look up the specific services bound to your application:

> ### Sample Code:  
> ```
> var xsenv = require('@sap/xsenv'); 
> 
> var services = xsenv.getServices({ 
>   hana: { tag: 'hdb' }, 
>   scheduler: function(service) { return service.label === 'jobs' }
> }); 
> 
> var hanaCredentials = services.hana; 
> var schedulerCredentials = services.scheduler;
> ```

The search criteria for the required services is specified in the query parameter to `getServices`. Each property of the query object specifies the query value for one service.

> ### Note:  
> `getServices` can return only the requested services; it cannot return any of the standard SAP HANA services \(for example, `hana`, `uaa`, `jobs`\) unless they are explicitly specified in the query parameter.

You can also pass a custom file from which you load a default service configuration. For example, the following example shows how to load defaults from the file `my-services.json`:

> ### Sample Code:  
> ```
> var xsenv = require('@sap/xsenv'); 
> 
> var services = xsenv.getServices({ 
>   hana: { tag: 'hana' }, 
>   uaa: { tag: 'uaa' } 
> }, 'my-services.json');
> ```



### Service Queries

Both `getServices` and `filterCFServices` use the same service query values.

**Query Values for getServices and filterCFservices**


<table>
<tr>
<th valign="top">

Query Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `{string}` 



</td>
<td valign="top">

Matches the service with the same service instance name \( `name` property\). Same as `{ name: '<string>' }`.



</td>
</tr>
<tr>
<td valign="top">

 `{object}` 



</td>
<td valign="top">

All properties of the given object should match corresponding service instance properties as they appear in `VCAP_SERVICES` 



</td>
</tr>
<tr>
<td valign="top">

 `{function}` 



</td>
<td valign="top">

A function that takes a service object as argument and returns true only if it is considered a match



</td>
</tr>
</table>

If an object is given as a query value, it may have the following properties:

**Object Properties for Query Values**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

The name of the service instance; the name you use to bind the service



</td>
</tr>
<tr>
<td valign="top">

 `label` 



</td>
<td valign="top">

Service name - the name shown by the command: “`xs marketplace`” 



</td>
</tr>
<tr>
<td valign="top">

 `tag` 



</td>
<td valign="top">

Should match any of the service tags



</td>
</tr>
<tr>
<td valign="top">

 `plan` 



</td>
<td valign="top">

The name of the service instance plan specified in the command: “`xs create-service`” 



</td>
</tr>
</table>



### Loading SSL Certificates

If SSL is configured in the run-time environment, it will provide one or more trusted CA certificates that applications can use to make SSL connections. If the certificates are available, the file paths to these certificates are listed in the *<XS\_CACERT\_PATH\>* environment variable separated by a path delimiter, for example, a colon \(:\) on Linux-based systems and a semi-colon \(;\) on Windows-based systems.

```
loadCerticates([certPath])
```

The `loadCertificates()` function enables you to load the certificates listed in the given path. If the `([certPath])` argument is not provided, `loadCertificates()` uses the *<XS\_CACERT\_PATH\>* environment variable instead. If neither `([certPath])` nor *<XS\_CACERT\_PATH\>* is defined, the `loadCertificates()` function returns “undefined”.

> ### Tip:  
> The `loadCertificates()` function is synchronous and returns an array even if only a single certificate is provided.

The following example shows how to load trusted CA certificates so they are used for all subsequent outgoing HTTPS connections:

> ### Sample Code:  
> ```
> var https = require('https'); 
> var xsenv = require('@sap/xsenv'); 
> 
> https.globalAgent.options.ca = xsenv.loadCertificates();
> ```

The following example shows how to load SSL certificates for use in SAP HANA:

> ### Sample Code:  
> ```
> var hdb = require('hdb'); 
> var xsenv = require('@sap/xsenv'); 
> 
> var client = hdb.createClient({ 
>   host : 'hostname', 
>   port : 30015, 
>   ca : xsenv.loadCertificates(), 
>   ... 
> });
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_dwh_dpt_vt"/>

## @sap/xsjs

The package enables SAP HANA XS Classic applications to run in the compatibility layer in the JavaScript run time for SAP HANA extended application services, advanced model \(SAP HANA XS advanced\).



### Usage

> ### Sample Code:  
> ```
> 'use strict'; 
> 
> var xsenv = require('@sap/xsenv'); 
> var xsjs = require('@sap/xsjs'); 
> 
> var port = process.env.PORT || 3000; 
> var options = xsenv.getServices({ 
>     uaa: 'xsuaa', 
>     hana: 'hana-hdi', 
>     jobs: 'scheduler', 
>     mail: 'mail', 
>     secureStore: 'secureStore' 
> })); 
> xsjs(options).listen(port); 
> 
> console.log('Node XS server listening on port %d', port);
> ```

The starting function takes an object that contains service credentials and application options.

**Property Options**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Default



</th>
<th valign="top">

Usage



</th>
</tr>
<tr>
<td valign="top">

 `rootDir` 



</td>
<td valign="top">

 `lib` 



</td>
<td valign="top">

Location of XS JavaScript files



</td>
</tr>
<tr>
<td valign="top">

 `rootDirs` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Same as `rootDir`, but an array of directories can be provided; overrides `rootDir` if both are set



</td>
</tr>
<tr>
<td valign="top">

 `uaa` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

UAA configuration necessary to enable authentication by JSON Web Tokens \(JWT\) and business-user propagation to SAP HANA



</td>
</tr>
<tr>
<td valign="top">

 `hana` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Object containing SAP HANA database connection parameters; used for database connectivity



</td>
</tr>
<tr>
<td valign="top">

 `secureStore` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Object containing SAP HANA database connection parameters; used for secure store connectivity



</td>
</tr>
<tr>
<td valign="top">

 `jobs` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Job scheduler connection parameters used to register jobs during application start up and later for updating job execution status when the job has finished



</td>
</tr>
<tr>
<td valign="top">

 `mail` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Mail options, used by XS JavaScript `$.net.Mail` API



</td>
</tr>
<tr>
<td valign="top">

 `maxBodySize` 



</td>
<td valign="top">

1 MB



</td>
<td valign="top">

Maximum body size accepted by xsjs. The value is passed to the bytes library for parsing. For more information, see **Bytes Utility** in the **Related Links** section below.



</td>
</tr>
<tr>
<td valign="top">

 `anonymous` 



</td>
<td valign="top">

 `false` 



</td>
<td valign="top">

Enable anonymous access; that is, access without user credentials



</td>
</tr>
<tr>
<td valign="top">

 `formData` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Special restrictions over form-data submitted to server



</td>
</tr>
<tr>
<td valign="top">

 `destinationProvider` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Custom function, synchronous or asynchronous, to be used when`$.net.http.readDestination` is called in XS JavaScript code.



</td>
</tr>
<tr>
<td valign="top">

 `ca` 



</td>
<td valign="top">

Certificates listed in the environment variable *<XS\_CACERT\_PATH\>* 



</td>
<td valign="top">

Trusted SSL certificates for any outgoing HTTPS connections, an array of loaded certificates



</td>
</tr>
<tr>
<td valign="top">

 `compression` 



</td>
<td valign="top">

 `true` 



</td>
<td valign="top">

By default text resources over 1,000 are compressed.



</td>
</tr>
<tr>
<td valign="top">

 `auditLog` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

Object containing audit-log credentials.



</td>
</tr>
<tr>
<td valign="top">

 `context` 



</td>
<td valign="top">

 `{}` 



</td>
<td valign="top">

Extend the default context in `@sap/xsjs` scripts



</td>
</tr>
<tr>
<td valign="top">

 `libraryCache` 



</td>
<td valign="top">

 `{}` 



</td>
<td valign="top">

Contains the `@sap/xsjs` libraries that should be cached.



</td>
</tr>
<tr>
<td valign="top">

 `redirectUrl` 



</td>
<td valign="top">

\-



</td>
<td valign="top">

If specified, a redirect to this URL is triggered when the root path is requested.

> ### Note:  
> If `@sap/xsjs` is behind a reverse proxy \(for example, an application router\), the value of this property should be aligned with the path-rewriting rules that may apply.



</td>
</tr>
</table>

SAP HANA XS advanced applications connect to SAP HANA with a fixed technical user provided by means of XS advanced services \(environment variables\). The actual \(business\) user of the application is retrieved from the JWT token and propagated to SAP HANA. The connection to the Job scheduler service is performed with a fixed technical user provided by the XS advanced service binding.



### hana

The `hana` object has the following properties:

**Property Options**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Usage



</th>
</tr>
<tr>
<td valign="top">

 `host` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

SAP HANA database host name



</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

SAP HANA database port number



</td>
</tr>
<tr>
<td valign="top">

 `user` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Technical user for database connections



</td>
</tr>
<tr>
<td valign="top">

 `password` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Password for technical user specified in `user` 



</td>
</tr>
<tr>
<td valign="top">

 `schema` 



</td>
<td valign="top">



</td>
<td valign="top">

If provided, sets current schema for database connections



</td>
</tr>
<tr>
<td valign="top">

 `connectWithLoggedUser` 



</td>
<td valign="top">



</td>
<td valign="top">

Possible values are `true` or `false` \(default\). If provided the database connection will be done made the SAML assertion contained in the JWT token of the logged user.

> ### Caution:  
> This option is provided only for the SAP HANA Cockpit transition to SAP HANA XS advanced. In general, this option should be avoided.



</td>
</tr>
<tr>
<td valign="top">

 `sqlcc` 



</td>
<td valign="top">



</td>
<td valign="top">

Object containing all SQLCC configurations as properties with name after SQLCC name used in XS JavaScript code



</td>
</tr>
<tr>
<td valign="top">

 `ca` 



</td>
<td valign="top">



</td>
<td valign="top">

Trusted SSL certificates intended explicitly for use by SAP HANA connections, or an array of loaded certificates. If not provided, the certificate from the service binding is used. If no certificates are available, the SAP HANA connection cannot be encrypted.



</td>
</tr>
</table>

The SQLCC property can be initialized from the bound services as shown in the following example:

> ### Sample Code:  
> ```
> options.hana.sqlcc = xsenv.getServices({ 
>   'com.sap.my.sqlcc_config': 'SQLCC__NAME', 
>   'com.sap.my.other_sqlcc_config': 'OTHER_SQLCC_UPS_NAME'
> });
> ```

To use it in your XS JavaScript code:

> ### Sample Code:  
> ```
> var connection = $.db.getConnection('com.sap.my.sqlcc_config');
> ```



### secureStore

The `secureStore` object has the following properties:

**Property Options**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Usage



</th>
</tr>
<tr>
<td valign="top">

 `host` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

SAP HANA database host name



</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

SAP HANA database port number



</td>
</tr>
<tr>
<td valign="top">

 `user` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Technical user for database connections



</td>
</tr>
<tr>
<td valign="top">

 `password` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Password for technical user specified in `user` 



</td>
</tr>
<tr>
<td valign="top">

 `schema` 



</td>
<td valign="top">



</td>
<td valign="top">

If provided, sets current schema for database connections



</td>
</tr>
</table>



### formData

The `formData` object has the following properties:

**Property Options**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Default



</th>
<th valign="top">

Usage



</th>
</tr>
<tr>
<td valign="top">

 `maxFilesSizeInBytes` 



</td>
<td valign="top">

10485760



</td>
<td valign="top">

restricts the total size of all the uploaded files.



</td>
</tr>
</table>



### mail

The `mail` object has the following properties:

**Property Options**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Usage



</th>
</tr>
<tr>
<td valign="top">

 `host` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

SMTP server host name



</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

Yes



</td>
<td valign="top">

SMTP server port number



</td>
</tr>
<tr>
<td valign="top">

 `ignoreTLS` 



</td>
<td valign="top">



</td>
<td valign="top">

 `True` or `false` \(default\). Defines if a STARTTLS command should be invoked if available by the mail server.



</td>
</tr>
<tr>
<td valign="top">

 `secure` 



</td>
<td valign="top">



</td>
<td valign="top">

 `True` or `false` \(default\). Defines if the connection should be over TLS/SSL.



</td>
</tr>
<tr>
<td valign="top">

 `connectionTimeout` 



</td>
<td valign="top">



</td>
<td valign="top">

Connection timeout in ms. Default =60000.



</td>
</tr>
<tr>
<td valign="top">

 `authMethod` 



</td>
<td valign="top">



</td>
<td valign="top">

Authentication method to use. Options are: “`PLAIN`”, “`LOGIN`”, or “`CRAM-MD5`” 



</td>
</tr>
<tr>
<td valign="top">

 `auth` 



</td>
<td valign="top">



</td>
<td valign="top">

Authentication credentials, for example: `{user: 'user', pass: 'pass'}`; default is no authentication.



</td>
</tr>
</table>



### destinationProvider

If your application requires different mechanisms for destination configuration, for example, dynamic configuration changes or dynamically adding new destinations to your application, you can provide your own function that retrieves these configurations from your storage. Support is provided for both synchronous and asynchronous destination provider function. The number of parameters your function has determines if the function is called synchronously or asynchronously. The signatures for both are as follows:

> ### Sample Code:  
> ```
> 
> function getDestinationSync(packagename, objectname, dtDescriptor) {
>  } 
> 
> function getDestinationAsync(packagename, objectname, dtDescriptor, callback) {
> }
> ```

**Parameter Options**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `packagename` 



</td>
<td valign="top">

The package of the destination supplied to `$.net.http.readDestination` 



</td>
</tr>
<tr>
<td valign="top">

 `objectname` 



</td>
<td valign="top">

The object name of the destination supplied to `$.net.http.readDestination` 



</td>
</tr>
<tr>
<td valign="top">

 `dtDescriptor` 



</td>
<td valign="top">

The object containing all properties contained in the corresponding HTTP destination configuration file \(`.xshttpdest`\), if available; otherwise “undefined” 



</td>
</tr>
<tr>
<td valign="top">

 `callback` 



</td>
<td valign="top">

Provided only in the asynchronous case and should be called by your provider function to return the destination or report error



</td>
</tr>
</table>



<a name="loio54513272339246049bf438a03a8095e4__section_bhp_hsl_mv"/>

## @sap/xsjs-test

This client library provides the unit-test framework for the XS JavaScript compatibility layer \(XS run time\). To use the `@sap/xsjs-test` tools in your MTA project, you will need to perform the following steps:

-   Declare a development dependency to `@sap/xsjs-test` in your XSJS application project \(for example, in the `package.json`\)

-   Your tests are located in test folder \(`test/`\) parallel to `package.json` and `lib/` 

-   Configure a `xstest` script in your application's `package.json` 

-   Run the test tools, for example with the command `npm run xstest` 


For the dependency to `@sap/xsjs-test`, you need to verify which version of `@sap/xsjs-test` is released and refer the released version. By establishing this developer dependency, you ensure that `@sap/xsjs-test` is installed only in the \(local\) development installation; it is not available for use in a productive installation. To avoid the necessity of any test dependencies, you can install the `@sap/xsjs-test` package on your development machine, for example, with the following command:

`npm install -g @sap/xsjs-test`

Normally the `xsjs` run-time files are located in the `xsjs/` folder, which means that the following paths are expected:

-   `<>/xsjs/package.json` 

-   `<>/xsjs/lib/` 

-   `<>/xsjs/test/`

    Contains your test scripts; if you choose to put the test scripts in a different folder, a special configuration is required.


Test script

There is a normal binary script defined in bin folder. The normal way would be to define a script in the application `package.json`, as illustrated in the following example:

> ### Sample Code:  
> ```
> "scripts": { 
>   "xstest" : "xstest" 
> } 
> ```

To start the XSJS unit tests from the command line, use the following command:

> ### Sample Code:  
> ```
> npm run xstest
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_atx_2vt_vt"/>

## @sap/xssec

The client security library includes the run-time-container security API for Node.js.

Authentication for SAP HANA Node applications relies on a special usage of the OAuth 2.0 protocol, which is based on central authentication at the SAP HANA User Authentication & Authorization \(UAA\) server that then vouches for the authenticated user's identity by means of a so-called OAuth Access Token. The current implementation uses as access token a JSON web token \(JWT\), which is a signed text-based token formatted according to the JSON syntax.

In a typical deployment scenario, your node application will consist of several parts, which appear as separate application packages in your manifest file, for example:

-   Database artifacts

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/db/</code>\) describes and defines the HANA database content

-   Application logic

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/js/</code>\) contains the application logic: code written in Node.js. This module can make use of this *Container Security API* for Node.js\).

-   UI client

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/web/</code>\) is responsible for the UI layer; this module can make use of the application router functionality \(defined in the file `xs-app.json`\).


> ### Note:  
> The application logic written in Node.js and the application router should be bound to one and the same UAA service instance so that these two parts use the same OAuth client credentials.

To use the capabilities of the container security API, add the package “`@sap/xssec`” to the dependencies section of your application's `package.json` file. To enable tracing, set the environment variable `DEBUG` as follows: `DEBUG=xssec:*`.



### Usage

In order to authenticate requests that reach the Node.js back end, `sap-xssec` offers the following mechanisms:

-   The container security API

-   The “passport” strategy included in `@sap/xssec`


To use the container security API, it is necessary to provide a JWT token. The examples below rely on users and credentials that you should substitute with the ones in your context. The typical use case for calling this API lies from within a container when an HTTP request is received. The authorization header \(with keyword “`bearer`” \) already contains an access token; you can remove the prefix bearer and pass the remaining string to the API as “`access_token`”, as illustrated in the following example:

> ### Sample Code:  
> ```
> xssec.createSecurityContext(access_token, xsenv.getServices({ uaa: 'uaa' }).uaa, function(error, securityContext) { 
>   if (error) { 
>       console.log('Security Context creation failed'); 
>       return; 
>   } 
>   console.log('Security Context created successfully'); 
> });
> ```

The example above uses the Node.js package `xsenv` to retrieve the configuration of the default services; the default services are read either from the environment variable *<VCAP\_SERVICES\>* or, if not set, from the default configuration file. However, only the required User Authentication & Authorization configuration \(`uaa`\) is passed to the method `createSecurityContext`.

The creation function `xssec.createSecurityContext` is used for an end-user token \(for example, with “grant type” `password` or `authorization_code`\) where user information is expected to be available within the token and, as a consequence, within the security context. `createSecurityContext` also accepts a token of grant type `client_credentials`, which enables the creation of a limited security context where certain functions are not available, as described in more detail in the Security API documentation below.

If you use the Node.js packages `express` and `passport`, you can plug in a ready-made authentication strategy, as illustrated in the following example:

> ### Sample Code:  
> ```js
> var express = require('express'); 
> var passport = require('passport'); 
> var JWTStrategy = require('@sap/xssec').JWTStrategy; 
> var xsenv = require('@sap/xsenv'); 
> ... 
> var app = express(); 
> ... 
> passport.use(new JWTStrategy(xsenv.getServices({uaa:{tag:'xsuaa'}}).uaa)); 
> 
> app.use(passport.initialize()); 
> app.use(passport.authenticate('JWT', { session: false }));
> ```

> ### Tip:  
> It is recommended to disable the session as in the example above. Each request comes with a JWT token so it is authenticated explicitly and identifies the user. If you still need the session, you can enable it but then you should also implement user serialization-deserialization and some sort of session persistency.



### Offline Validation

The trust relationship required for offline validation is created by binding the UAA service instance to your application. The key used to validate tokens is included in the credentials section of the environment variable *<VCAP\_SERVICES\>*. By default, the offline validation check in Cloud environments only accepts tokens intended for the same OAuth 2.0 client in the same UAA subaccount. However, if an application needs to consume tokens that were issued either for different OAuth 2.0 clients or for different subaccounts, it is possible to specify an access control list \(ACL\) entry in the environment variable *<SAP\_JWT\_TRUST\_ACL\>*, as illustrated in the following example:

> ### Sample Code:  
> Client ACL in *<SAP\_JWT\_TRUST\_ACL\>* Environment Variable
> 
> ```
> SAP_JWT_TRUST_ACL: [ {"clientid":"<OAuth_2.0_client_ID>","subaccount":"<subaccount>"},...]
> ```

The name of the OAuth 2.0 client has the prefix “`sb-`”; the corresponding content is a JSON string that contains an array of subaccounts and OAuth 2.0 clients. To establish trust with **any** OAuth 2.0 client and/or subaccounts, you can use an asterisk \(\*\). For security reasons, however, this is not recommended in a productive environment. The value for the subaccount is “`uaa`”.

> ### Note:  
> Changes have been made to the Java client libraries `java-security` and `spring-xsuaa` and the container security API for Node.js \>=3.0.6. If you plan to use these libraries or the security API, please note that it is no longer possible to use the parameter `SAP_JWT_TRUST_ACL` to specify a dedicated access control list \(ACL\) for JWT tokens. Changes also apply regarding the granting of security scopes, which are defined and granted in the application security descriptor \(`xs-security.json`\). For example, if a business application A wants to call another application B, it is now mandatory that application B grants at least one scope to the calling business application A. For more information about security scopes, see the *Application Security Descriptor Configuration Syntax* in *Related Information* below.



### Container Security API

The complete details of the container security API including all parameters and options are available in the README file included in the `@sap/xssec` package.

**Container Security API**


<table>
<tr>
<th valign="top">

API



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `createSecurityContext` 



</td>
<td valign="top">

Creates the “security context” by validating the received access token against credentials put into the application's environment via the UAA service binding



</td>
</tr>
<tr>
<td valign="top">

 `getLogonName` 



</td>
<td valign="top">

Returns the user's logon name \*



</td>
</tr>
<tr>
<td valign="top">

 `getGivenName` 



</td>
<td valign="top">

Returns the user's given \(first\) name \*



</td>
</tr>
<tr>
<td valign="top">

 `getFamilyName` 



</td>
<td valign="top">

Returns the user's family name \*



</td>
</tr>
<tr>
<td valign="top">

 `getEmail` 



</td>
<td valign="top">

Returns the user's email address \*



</td>
</tr>
<tr>
<td valign="top">

 `checkLocalScope` 



</td>
<td valign="top">

Checks a scope that is published by the current application in the `xs-security.json` file. Returns “true” if the checked scope is included in the user's authorization scopes \(otherwise “false”\)



</td>
</tr>
<tr>
<td valign="top">

 `checkScope` 



</td>
<td valign="top">

Checks a scope that is published by an application. Returns “true” if the checked scope is included in the user's authorization scopes \(otherwise “false”\)



</td>
</tr>
<tr>
<td valign="top">

 `getToken` 



</td>
<td valign="top">

Returns a token that can be used to connect to the SAP HANA database. If the token that the security context has been instantiated with is a foreign token \(meaning that the OAuth client contained in the token and the OAuth client of the current application do not match\), “`null`” is returned instead of a token.



</td>
</tr>
<tr>
<td valign="top">

 `getHdbToken` 



</td>
<td valign="top">

Returns a token that can be used to connect to the SAP HANA database. If the token that the security context has been instantiated with is a “foreign” token \(the OAuth client contained in the token and the OAuth client of the current application do not match\), “`null`” is returned instead of a token.



</td>
</tr>
<tr>
<td valign="top">

 `requestTokenForClient` 



</td>
<td valign="top">

Requests a token with `grant_type=user_token` from another client. The requesting client must also have `grant_type=user_token`, and the current user token must include the authorization scope `uaa.user`.



</td>
</tr>
<tr>
<td valign="top">

 `hasAttributes` 



</td>
<td valign="top">

Returns “`true`” if the token contains any user attributes; otherwise “`false`”.



</td>
</tr>
<tr>
<td valign="top">

 `getAttribute` 



</td>
<td valign="top">

Returns the attribute exactly as it is contained in the access token. If no attribute with the given name is contained in the access token, “`null`” is returned. If the token that the security context has been instantiated with is a foreign token \(the OAuth client contained in the token and the OAuth client of the current application do not match\), “`null`” is returned regardless of whether the requested attribute is contained in the token or not.



</td>
</tr>
<tr>
<td valign="top">

 `getAdditionalAuthAttribute` 



</td>
<td valign="top">

Requires the `name` of the additional authentication attribute requested. Returns the requested attribute exactly as it is contained in the access token. If no attribute with the given `name` is contained in the access token, `null` is returned.

> ### Note:  
> Additional authentication attributes are also returned in “foreign” mode \(in contrast to `getAttribute`\).



</td>
</tr>
<tr>
<td valign="top">

 `isInForeignMode` 



</td>
<td valign="top">

Returns “`true`” if the token, that the security context has been instantiated with, is a foreign token that was not originally issued for the current application, otherwise “`false`”.



</td>
</tr>
<tr>
<td valign="top">

 `getIdentityZone` 



</td>
<td valign="top">

Returns the identity zone that the access token has been issued for



</td>
</tr>
<tr>
<td valign="top">

 `getExpirationDate` 



</td>
<td valign="top">

Returns the expiration date of the access token as a Javascript “Date” object



</td>
</tr>
<tr>
<td valign="top">

 `getCloneServiceInstanceId` 



</td>
<td valign="top">

Returns the id of the cloned service instance, if the XSUAA broker plan is used



</td>
</tr>
<tr>
<td valign="top">

 `getGrantType` 



</td>
<td valign="top">

Returns the grant type of the JWT token, for example: `authorization_code`, `password`, `client_credentials`, etc.



</td>
</tr>
</table>

> ### Note:  
> \* Not available for tokens of grant type `client_credentials`



<a name="loio54513272339246049bf438a03a8095e4__section_mvj_4kt_vt"/>

## @sap/xss-secure

This is a Node.js package that includes the cross-site scripting \(XSS\) security implementation taken from SAP UI5.



### Usage

> ### Sample Code:  
> ```
>  var xsssecure = require('@sap/xss-secure'); 
> ```

The `@sap/xss-secure` package includes the following APIs:

-   `encodeCSS`

    For Cascading Style sheets

-   `encodeHTML`

    For HTML markup

-   `encodeJS`

    For JavaScript code

-   `encodeURL`

    For URL components, for example, parameter names or values

-   `encodeXML`

    For XML code


Cross-site Scripting \(XSS\) is the name of a class of security vulnerabilities that can occur in Web applications. It summarizes all vulnerabilities that allow an attacker to inject HTML Markup or JavaScript into the affected Web application's front-end. XSS can occur whenever the application dynamically creates its HTML, JavaScript, or CSS \(either in the back end or in the front-end part of the application in the user's Web browser\), and values controlled by the attacker are used in this process. If this happens, the values are included in the generated HTML, JavaScript, or CSS without proper validation or encoding. As a result, an attacker is able to include arbitrary HTML, JavaScript, or CSS into an application's client front end; this code is, in turn, rendered by the victim's Web browser and, in this way, interpreted in the victim's current authentication context.



<a name="loio54513272339246049bf438a03a8095e4__section_atm_w5l_mv"/>

## @sap/e2e-trace

SAP Passports allow the identification of a specific request in an end-to-end scenario involving several components, which need to communicate with each other. The client sends a special header containing the SAP Passport \(a hex string with a special structure\) to the first component. The client can send the SAP passport by means of a browser plug in or the front-end component of an SAPUI5 application. Whenever an application component receives an SAP Passport, this component should ensure that the unique identifiers of the SAP Passport are included in its log and trace files, update the SAP passport with component-specific data, and then forward it to the next system.

An application receives an SAP Passport in the `@sap/passport` header. The same header is used when the SAP Passport is forwarded to another system with the HTTP protocol. If the SAP passport is sent to SAP HANA, the SAP Passport should be set as the `'SAP_PASSPORT'` session variable of the database connection.

To load the `@sap/e2e-trace` package, use the following command:

> ### Sample Code:  
> ```
> var SAPPassport = require('@sap/e2e-trace').Passport;
> ```

The code in the following example shows how to create an instance of an SAP Passport:

> ### Sample Code:  
> ```
> function requestHandler(req, res) { 
>   var encodedPassport = req.headers[SAPPassport.HEADER_NAME]; 
>   if (encodedPassport) { 
>     var passport = new SAPPassport(encodedPassport); 
>   } 
> }
> ```

The library provides the constant `SAPPassport.HEADER_NAME` for the `'@sap/passport'` header; the passport variable is an instance which you can use to read \(or modify\) the SAP Passport in your application component. The following code example shows how to read the unique identifiers of an SAP Passport:

> ### Sample Code:  
> ```
> var identifiers = passport.readUniqueIdentifiers();
> ```

The returned value \(assigned to the identifiers variable\) is an object that has the following properties: `transactionID`, `rootContextID`, `connectionID`, and `connectionCounter`. These fields of the SAP Passport must be present in the logs and traces of the application component. If you are using the `@sap/logging` library, refer to its documentation to check if the specific version of the library is capable of handling SAP Passports.

To see how to update the SAP Passport before forwarding it to the next application component, have a look at the following code example:

> ### Sample Code:  
> ```
> passport.update({ 
>   previousComponent: 'my-application', 
>   connectionID: '00112233445566778899AABBCCDDEEFF', 
>   connectionCounter: 36 
> });
> ```

This method takes an object with the following **mandatory** properties:

**Mandatory SAP Passport Properties**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Value



</th>
<th valign="top">

Semantics



</th>
</tr>
<tr>
<td valign="top">

 `previousComponent` 



</td>
<td valign="top">

ASCII string \(up to 32 characters\)



</td>
<td valign="top">

The name of the current component which is about to make an outbound connection to another component.



</td>
</tr>
<tr>
<td valign="top">

 `connectionID` 



</td>
<td valign="top">

GUID \(16-byte hex\)



</td>
<td valign="top">

Every connection between the current component and the next component should have an ID which is passed as that property.



</td>
</tr>
<tr>
<td valign="top">

 `connectionCounter` 



</td>
<td valign="top">

Positive integer \(up to 4 bytes\)



</td>
<td valign="top">

The amount of time for the connection with the given `connectionID` is being reused.



</td>
</tr>
</table>

> ### Restriction:  
> The SAP HANA database has a limitation regarding the size of the SAP Passport. It is recommended to call the method `passport.compact();` before forwarding an SAP Passport to SAP HANA.

The following code example shows how to generate a hex string from the updated SAP Passport; the SAP Passport can be sent to other components in this format:

> ### Sample Code:  
> ```
> var http = require('http'); 
> var url = require('url'); 
> 
> var encodedPassport = passport.serialize(); 
> 
> var options = url.parse('http://my-host:1234/my/path'); 
> options.headers = {};
> options.headers[SAPPassport.HEADER_NAME] = encodedPassport; 
> 
> var request = http.request(options); 
> request.on('error', function (err) { /* ... */ }); 
> request.on('response', function (response) { /* ... */ }); 
> request.end();
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_wxk_pqk_xz"/>

## @sap/node-vsi

The `@sap/node-vsi` package contains the Virus Scan Interface \(VSI\) binding for Node.js. The package also includes the native libraries required to run on Windows, Linux, and MacOS operating systems.

The following example shows how to use `@sap/node-vsi` to scan for the standard test file from the European Institute for Computer Antivirus Research at “www.eicar.com”. All anti-virus scanners must be able not only to find the file but also detect that it is a virus:

> ### Sample Code:  
> ```
> var vsi = require('@sap/node-vsi'); 
> var vsiProfile = vsi.vsiProfile; 
> var v = new vsiProfile(""); 
> v.scanBytes("eicar.txt","X5O!P%@AP[4\\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*", 68); 
> console.log("\nResult of eicar scan is rc " + v.getLastErrorCode() + " (" + v.getScanErrorName() + ") with error message: \n" + v.getLastError() + "\n" );
> ```



### Getting Started

To start using the VSI `@sap/node-vsi` run the following command from your project directory:

```
$ var vsi = require('@sap/node-vsi');

```



<a name="loio54513272339246049bf438a03a8095e4__section_mn4_w5l_mv"/>

## @sap/sds-deploy

The `@sap/sds-deploy` package includes the Node.js client for the deployment of application projects for the SAP HANA Streaming Analytics option. The `@sap/sds-deploy` library compiles the Continuous Computation Language \(CCL\) content of a Streaming Analytics project \(consisting of a CCL file and an optional CCR file\) and deploys the Streaming Analytics project to the Streaming Analytics service installed with the SAP HANA platform.

The Streaming Analytics application project is mapped to a Streaming Analytics module in the multi-target application \(MTA\). The Streaming Analytics application project consists of two configuration files:

-   `mySDS_Project-Definition.ccl`

    The Streaming Analytics project-definition file is written in Continuous Computation Language \(CCL\), which is the primary event-processing language of SAP HANA Streaming Analytics. You define a Streaming Analytics project using CCL, which is a language that is based on Structured Query Language \(SQL\), and adapted for stream processing.

-   `mySDS_Project_Configuration.ccr`

    A project-configuration file \(`.ccr`\) is an XML document that is used to control specific run-time properties of a Streaming Analytics project, including the data stream's URI bindings as well as any adapter properties, parameter values, and advanced deployment options.


The following example of a simple `.ccl` file shows some code that runs a simple Tuple test:

> ### Sample Code:  
> Example `random_tuple_test2.ccl`
> 
> ```
> CREATE INPUT WINDOW InputStream1 SCHEMA ( Column1 integer , Column2 integer , Column3 integer , Column4 string ) PRIMARY KEY(Column1,Column2,Column3,Column4) KEEP 10000 ROWS; 
> 
> ATTACH INPUT ADAPTER RandomTuples2 TYPE randomtuplegen_in TO InputStream1 PROPERTIES Rate =10000 , RowCount =0 , SecondDateFormat = '%Y-%m-%d %H:%M:%S' , MsDateFormat = '%Y-%m-%d %H:%M:%S' ; 
> 
> CREATE OUTPUT STREAM OutStream1 AS SELECT InputStream1.Column1 SimpleResultExpression2 , InputStream1.Column2 SimpleResultExpression1 FROM InputStream1; 
> 
> CREATE OUTPUT STREAM OutStream2 AS SELECT InputStream1.Column1 SimpleResultExpression2 , InputStream1.Column2 SimpleResultExpression1 FROM InputStream1;
> ```

The following code example shows the contents of the corresponding `.ccr` file for the `random_tuple_test2.ccl`:

> ### Sample Code:  
> Example `random_tuple_test2.ccl`
> 
> ```
> <?xml version="1.0" encoding="UTF-8"?>
> <Configuration xmlns="http://www.sybase.com/esp/project_config/2010/08/">
>  <Deployment>
>     <Project ha="false">
>       <Options>
>         <Option name="time-granularity" value="5"/>
>         <Option name="debug-level" value="7"/>
>         <Option name="ignore-config-topology" value="false"/>
>       </Options>
>       <Instances>
>         <Instance>
>           <Failover enable="false"/>
>           <Affinities/>
>         </Instance>
>       </Instances>
>     </Project>
>   </Deployment>
> </Configuration>
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_cgq_w5l_mv"/>

## @sap/audit-logging

Provides audit logging functionality for Node.js applications.

Audit logging concerns writing entries in a specific format to a log storage. The entries written to the audit log concern any events of significant importance, for example, security events which may impact the confidentiality, the integrity, or the availability of a system. Access to sensitive personal data \(both reading and altering\) such as bank accounts, political opinion, health status is also an event that is written to the audit log. Audit logs are not the same as ordinary log files. Ordinary log files are used by the system administrator who need to keep track of the state of a system; audit logs are read by an auditor. Audit logs are subject to legal requirements, which in some countries are stricter than in others. In general, the events that are supposed to be recorded in the audit log can be grouped into the following categories:

-   Changes to system configurations \(which may have significant effect on the system itself\)

-   Access to sensitive data \(related to data privacy\)

-   General security events \(for example, starting or stopping a system, failed authorization checks, etc.\)


> ### Tip:  
> For more detailed information about the audit-log NPM package, see the `README.md` file included in the `@sap/audit-logging` package.



<a name="loio54513272339246049bf438a03a8095e4__section_p4f_zxd_sy"/>

## @sap/xs-msg

Provides messaging capabilities with a message broker. This package supports the RabbitMQ message broker with the following protocols:

-   amqp v091

-   amqp v100

-   mqtt v311




### Prerequisites

A message broker must be available, for example, RabbitMQ.



### Usage

The package folder `./examples` includes some test programs that can be used if a broker can be reached locally at the protocol-specific default port. The `examples/cfg` folder also includes some sample configurations.

The following example shows how to create a new messaging client and set it up to start consuming incoming messages:

> ### Sample Code:  
> ```js
> const msg = require('@sap/xb-msg'); 
> const env = require('@sap/xb-msg-env'); 
> 
> /* get options from cf/xsa environment */ 
> const options = env.msgClientOptions('msg-instance-01', ['MyInpA'], []);
> 
> /* start messaging */ 
> const client = new msg.Client(options); 
> 
> client.istream('MyInpA') 
>    .on('subscribed', () => { 
>        console.log('subscribed'); 
>    })
>    .on('data', (message) => { 
>        console.log('message: ' + message.payload.toString()); 
>        message.done(); 
>    }); 
> 
> client.connect();
> ```

The following example shows how to create a new messaging client and set it up to start producing messages:

> ### Sample Code:  
> ```js
>  const msg = require('@sap/xb-msg'); 
> const env = require('@sap/xb-msg-env'); 
> 
> /* get options from cf/xsa environment */ 
> const options = env.msgClientOptions('msg-instance-01', [], ['MyOutB']);
> 
> /* start messaging */ 
> const client = new msg.Client(options); 
> 
> client.ostream('MyOutA') 
>     .on('ready', () => { 
>         send(); 
>     }) 
>     .on('drain', () => { 
>         send(); 
>     }) 
>     .on('error', (error) => { 
>         console.log(error); 
>     }); 
> 
> client.connect();
> ```

After the client is created and connected the application can start writing to \(and/or reading from\) the named stream instances. Based on the client options, one or more connections are created for each of the supported protocols and each providing multiple inbound or outbound streams. All stream IDs must be unique in the scope of a client instance.

> ### Note:  
> For more information about features and functionality, see the `README.md` file included in the Node.js package `@sap/xb-msg`.

Connections via `'net'` and `'tls`' are supported for all protocols. For MQTT, WebSocket can be used either with `'https'` \(wss\) or `'http'` \(ws\). If multiple settings are provided, the order of preference is as follows: `'tls'`, `'net'`, `'wss'`, and `'ws'`.



<a name="loio54513272339246049bf438a03a8095e4__section_tv5_wkj_tgb"/>

## @sap/xb-msg-env

This package provides the functions needed to set up messaging client options from Cloud Foundry environment variables.

The following clients are supported:

-   `@sap/xb-msg`

    A protocol-agnostic API with multiple destinations per single client

-   `@sap/xb-msg-amqp-v100`

    A protocol-specific API with a single connection per client

-   `@sap/xb-msg-amqp-v091`

    A protocol-specific API with a single connection per client

-   `@sap/xb-msg-mqtt-v311`

    A protocol-specific API with a single connection per client.


`@sap/xb-msg-env` can use the following environment variables:


<table>
<tr>
<th valign="top">

Environment Variable



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 *<VCAP\_SERVICES\>* 



</td>
<td valign="top">

Defines bindings to RabbitMQ or Enterprise Messaging services



</td>
</tr>
<tr>
<td valign="top">

 *<SAP\_XBEM\_SERVICE\_LABEL\>* 



</td>
<td valign="top">

Defines details of an alternative service label for Enterprise Messaging



</td>
</tr>
<tr>
<td valign="top">

 *<SAP\_XBEM\_BINDINGS\>* 



</td>
<td valign="top">

Defines details of incoming and \(or\) outgoing message streams \(`"istreams"` and `"ostreams"`\)



</td>
</tr>
</table>



### Prerequisites

See the `README` file in the NPM package for information about the versions of the various messaging packages required, for example, `@sap/xb-msg` version "0.2.3".



### Usage

The following example shows how to use environment variables for one Rabbit MQ instance named '`myService`'. The messaging service's incoming and outgoing message streams can be maintained as `"inputs"` and `"outputs"` in another environment variable named `SAP_XBEM_BINDINGS`. In the following example, one output named '`myOutA`' is defined.

> ### Sample Code:  
> ```
> {
>   "VCAP_SERVICES": {
>     "rabbitmq": [
>         {
>             "credentials": {
>                 "hostname": "10.11.11.11",
>                 "ports": {
>                     "15672/tcp": "8888",
>                     "5672/tcp": "9999"
>                 },
>                 "port": "9999",
>                 "username": "user",
>                 "password": "password",
>                 "uri": "amqp://user:password@10.11.11.11:9999"
>             },
>             "syslog_drain_url": null,
>             "volume_mounts": [],
>             "label": "rabbitmq",
>             "provider": null,
>             "plan": "v3.6-container",
>             "name": "myService",
>             "tags": [
>                 "rabbitmq",
>                 "mbus",
>                 "pubsub",
>                 "amqp"
>             ]
>         }
>     ]
>   },
>   "SAP_XBEM_BINDINGS": {
>     "outputs": {
>       "myOutA" : {
>         "service": "myService",
>         "address": "topic:Cars/Velocity/milesPerHour",
>         "reliable": false
>       }
>     }
>   }
> }
> ```

The following call can be used to provide the client options for `@sap/xb-msg`:

```
const env = require('@sap/xb-msg-env'); 
const opt = env.msgClientOptions('myService', [], ['myOutA']);
```

The generated options for a `@sap/xb-msg` client using the `amqp-v091` protocol should look like the following example:

> ### Sample Code:  
> Messaging Client Options for `@sap/xb-msg`
> 
> ```
> 
> { "destinations": [ 
>     { 
>       "name": "myService", 
>       "type": "amqp-v091", 
>       "net": { 
>         "host": "10.11.11.11", 
>         "port": 9999 
>       }, 
>       "sasl": { 
>         "user": "user", 
>         "password": "password" 
>       }, 
>       "amqp": { 
>         "vhost": "/" 
>       }, 
>       "istreams": { 
>       }, 
>       "ostreams": { 
>         "out": { 
>           "channel": 1, 
>           "exchange": "amq.topic", 
>           "routingKey": "Cars.Velocity.milesPerHour", 
>           "confirms": false 
>         }
>       }
>     } 
>   ] 
> }
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_fcw_zxd_sy"/>

## @sap/xb-msg-amqp-v091

This package provides a client implementation for AMQP v0.9.1.

A single client instance represents one connection to the broker. Either TLS or NET socket is used depending on the options defined for the client . The API works completely asynchronous based on callbacks, often providing also “done” \(resolve\) and “failed” \(reject\) callbacks. This means it would be simple to use “Promise” objects in the application even if the client library so far does not use it. AMQP v0.9.1 defines classes and methods \(like remote procedure calls\). Unfortunately, some of them do not allow a key-based mapping of responses to requests. Hence, for those methods the client has to wait for the response before a second request can be sent. The client encapsulates this and behaves always asynchronously for the caller.



### Prerequisites

A message broker must be available, for example, RabbitMQ.



### Usage

The package folder `./examples` includes some test programs that demonstrate the following usage scenarios:

-   How to use the `publisher.js` and `subscriber.js` APIs

-   How to use the unified streams `producer.js` and `consumer.js`


All examples support the use of custom settings, for example, to use a remote host or to try different stream settings. Settings can be provided in a JavaScript \(`.js`\) file that is included as a command-line parameter for the `node` command. The file exports a client-option object. Defaults will still be used for undefined fields.

> ### Note:  
> For more information about features and functionality, see the `README.md` file included in the Node.js package `@sap/xb-msg-amqp-v091`.

The following example shows how to create a new client instance:

> ### Sample Code:  
> ```js
> const options = { 
>     tls: { 
>         host: 'localhost',  
>         port: 5671,  
>         ca: [  
>             fs.readFileSync('../../../truststore/cacert.pem'),  
>             fs.readFileSync('../../../truststore/cert.pem')  
>         ]  
>     },  
>     net: {  
>         host: 'localhost',  
>         port: 5672,  
>     },  
>     sasl: {  
>         user: 'guest',  
>         password: 'guest'  
>     },  
>     amqp: {  
>         vhost: '/',  
>     } 
> }; 
> const client = new AMQP.Client(options);
> ```

> ### Tip:  
> It is also possible to provide connection data as a URI or an array of URIs.

In the following example, the client starts by using the first URI in the array to establish a connection. If the connection attempt is not successful, the client tries further URIs automatically in the sequence provided until a connection can be established. If the client fails with all provided URIs, it stops and waits for another explicit call to connect. At this point an event 'disconnected' is raised.

> ### Sample Code:  
> Client Connection Details as URLs
> 
> ```js
> const options = { 
>     uri: [ 
>          'amqp://guest:guest@localhost:5672/vh111', 
>          'amqp://guest:guest@localhost:5672/vh222' 
>     ] 
> };
> const client = new AMQP.Client(options);
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_ox3_nlr_pgb"/>

## xb-msg-amqp-v100

This package provides a messaging client as well as the classes required to create a server for AMQP 1.0.



### Prerequisites

A message broker must be available, for example, RabbitMQ, and the AMQP 1.0 plug-in.



### Usage

A single client instance represents one connection to the broker. Either TLS or NET socket is used depending on defined client options. In addition to plain TCP/IP, WebSocket is also supported, with and without OAuth 2.0, grant flows `ClientCredentialsFlow`, and `ResourceOwnerPasswordCredentialsFlow`.

The API works asynchronously based on callbacks, typically providing done \(`resolve`\) and failed \(`reject`\) callbacks. This means it is easy to use Promise objects in the application even if this library does not currently use them.

The package folder `./examples` includes some test programs that demonstrate the following usage scenarios:

-   How to use the client as a “producer”, a “consumer”, or a “counter” 

-   How to configure a server with basic settings for a protocol gateway


> ### Note:  
> For more information about features and functionality, see the `README.md` file included in the Node.js package `@sap/xb-msg-amqp-v100`.

All client examples run with the provided default settings, for example, with RabbitMQ installed at `localhost:5672` with user “guest/guest”, and with the AMQP 1.0 plug-in enabled. Alternatively, the producer can run in combination with the “gateway” example. All examples can be configured with custom settings, for example, to use a remote host or to try different stream settings. The modified settings can be included in a JavaScript file, for example, `my-options.js`, that is provided as a command-line parameter, as illustrated in the following example, where the settings file is located in the `config\` directory used for all the examples:

```
node .\examples\producer.js ..\config\my-options.js
```

The following example can be used to start testing:

> ### Note:  
> The data section is only for use with the example programs; it is ignored by the client.

> ### Sample Code:  
> ```js
> 'use strict'; 
> 
> module.exports = { 
>     net: {
>         host : '127.0.0.1', 
>         port : 5672 
>     }, 
>     sasl: { 
>         mechanism : 'PLAIN', 
>         user : 'guest', 
>         password : 'guest' 
>     }, 
>     data: { 
>         source : 'q001', // a queue name, source address for a receiver
>         target : 'q002', // a queue name, target address for a sender 
>         payload : new Buffer.allocUnsafe(50).fill('X'), 
>         maxCount : 10000, 
>         logCount : 1000 
>     } 
> };
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_fy2_yxd_sy"/>

## @sap/xb-msg-mqtt-v311

This package provides a client implementation for MQTT v3.1.1.

A single client instance represents one connection to the broker, and the connection uses either TLS or NET socket depending on the options defined in the client connection. Since the API works asynchronously based on callbacks, often providing “done” \(resolve\) and “failed” \(reject\) callbacks, it should be simple to use Promise objects in the application even if the client library does not yet do so.



### Prerequisites

A message broker must be available, for example, RabbitMQ, with the MQTT plug-in enabled.



### Usage

The package folder `./examples` includes some test programs that demonstrate the following usage scenarios:

-   How to use the `publisher.js` and `subscriber.js` APIs

-   How to use the unified streams `producer.js` and `consumer.js`


All examples support the use of custom settings, for example, to use a remote host or to try different stream settings. Settings can be provided in a JavaScript \(`.js`\) file provided as command-line parameter to the `node` command. The file exports a client-option object. Defaults will still be used for undefined fields.

> ### Note:  
> For more information about features and functionality, see the `README.md` file included in the Node.js package `@sap/xb-msg-mqtt-v311`.

The following example shows how to create a new client instance using plain TCP:

> ### Sample Code:  
> ```js
> const options = { 
>    net: { 
>        host: 'localhost', 
>        port: 1883 
>    }, 
>    credentials: { 
>        user: '', 
>        password: '' 
>    } 
> }; 
> 
> const client = new MQTT.Client(options);
> ```

The following example shows how to create a new client instance using plain TCP with TLS connection:

> ### Sample Code:  
> ```js
> const options = { 
>    net: { 
>        host: 'localhost', 
>        port: 1883 
>        ca: [ 
>            fs.readFileSync('../../../truststore/cacert.pem'), 
>            fs.readFileSync('../../../truststore/cert.pem')
>        ]
>    }, 
>    credentials: { 
>        user: '', 
>        password: '' 
>    }, 
>    mqtt: { 
>        clientID : '', 
>        cleanSession : true, 
>        keepAlive : 30 
>    } 
> }; 
> 
> const client = new MQTT.Client(options);
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_lk1_dtq_sy"/>

## @sap/site-entry

This component is the Web entry for Fiori Launchpad portal sites. It includes an `approuter` component that serves as its Web server for requests from client-side resources and back-end calls. This component uses the portal-service that runs in the environment.



### Usage

Create the folder structure shown in the following example:

> ### Sample Code:  
> Application Sources Folder Structure
> 
> ```
> <site-entry-folder-name>/
> | - package.json
> | - xs-app.json
> 
> ```

The following code sample shows the contents of the application package descriptor \(`package.json`\):

> ### Sample Code:  
> `package.json`
> 
> ```
> {
>   "engines": {
>     "node": ">=4.0.0"
>   },
>   "name": "site-entry",
>   "dependencies": {
>     "@sap/site-entry": "^1.9.1"
>   },
>   "scripts": {
>     "start": "node --harmony node_modules/@sap/site-entry/server.js"
>   }
> }
> 
> ```

In the application descriptor `xs-app.json`, add the route to your SAPUI5 application's static resources:

> ### Sample Code:  
> Application Descriptor \(`xs-app.json`\)
> 
> ```
> {
> "source": "^/app1/sap/demo/(.*)",
> "target": "$1",
> "localDir": "app1/sap/demo/",
> "cacheControl": "public, max-age=31536000,must-revalidate"
> }
> 
> ```

The `mtad.yaml` file must contain the following information:

-   The site-entry module needs to be bound to the `portal-service` service; it should require a resource of the following type: `com.sap.portal.site-host`.

-   The path to the SAPUI5 that is deployed on the model host

-   The path to the XS User Account and Authentication \(UAA\) system


> ### Sample Code:  
> Application Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> …
> modules:
>  - name: site-entry-<unique site id>
>    parameters:
>       memory: 64M
>    requires:
>     - name: sap-portal-services-host-<unique site id>
>     - name: myuaa
>     - name: sapui5-provider
>       properties:
>          sapui5url: ~{url}
>    type: javascript.nodejs
>  - name: site-content-<unique site id>
>    parameters:
>       memory: 32M
>    requires:
>     - name: sap-portal-services-client-<unique site id>
>     - name: myuaa
>    type: com.sap.portal.site-content
> resources:
>  - name: sap-portal-services-host-<unique site id>
>    parameters:
>       config:
>          siteId: <unique site id>
>    type: com.sap.portal.site-host
>  - name: myuaa
>    parameters:
>       service-plan: space
>    type: com.sap.xs.uaa
>  - name: sapui5-provider
>    parameters:
>       provider-id: com.sap.ui5.dist.sapui5-dist-xsa.XSAC_UI5_FESV3:sapui5_fesv3
>       version: '>=1.42.0'
>       provider-nid: mta
>    type: configuration
>  - name: sap-portal-services-client-<unique site id>
>    parameters:
>       config:
>          siteId: <unique site id>
>    type: com.sap.portal.site-content
> 
> ```



<a name="loio54513272339246049bf438a03a8095e4__section_pth_dtq_sy"/>

## @sap/site-content-deployer

This component is combined with the `@sap/site-entry` node module, which in turn acts as the Web-entry server for the Fiori Launchpad portal site. This component is used to deploy the Fiori Launchpad portal site configuration \(for example, the configuration of tiles, groups and catalogs\) into the run-time environment. This component uses the portal-service that runs in the run-time environment.



### Usage

Create the folder structure shown in the following code sample and copy the `manifest.json` file of your SAPUI5 application to your app folder, `MySAPUI5App`, as illustrated in the following example:

> ### Sample Code:  
> Application Sources Folder Structure
> 
> ```
> <site-content-deployer-folder-name>/
> |- package.json
> |- applications/
> |  \- MySAPUI5App/
> |     |- manifest.json
> |     \- i18n/ 
> \- src/
>    |- site-content.json
>    \- i18n/
>  
> 
> ```

The following code is an example of a `package.json` file:

> ### Sample Code:  
> Application Package Descriptor \(`package.json`\)
> 
> ```
> {
>   "engines": {
>     "node": "4.x"
>   },
>   "name": "site-content-deployer",
>   "version": "1.9.1",
>   "description": "portal deployer package",
>   "dependencies": {
>     "@sap/site-content-deployer": "^1.9.1"
>   },
>   "scripts": {
>     "start": "node --harmony node_modules/@sap/site-content-deployer/deploy.js"
>   }
> }
> 
> ```

The `site-content-deployer` module must be bound to the `portal-service` service. For example, in the `mtad.yaml` file, the `site-content-deployer` should require a resource of type “`com.sap.portal.site-content`”, as illustrated in the following example:

> ### Sample Code:  
> Application Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> …
> modules:
> - name: site-content-deployer-<unique site id>
>    type: javascript.nodejs
>    requires:
>     - name: sap-portal-services-client-<unique site id>
> …  
> resources:
> - name: sap-portal-services-client-<unique site id>
>    type: com.sap.portal.site-content
>   parameters:
>       config:
>          siteId: <unique site id>
> 
> ```

For more information about developing Fiori Launchpad modules, see *Related Information*.



<a name="loio54513272339246049bf438a03a8095e4__section_hs2_fpt_2z"/>

## @sap/site-app-server

This component is a Web server for static resources used by applications that run in a Fiori Launchpad portal site. This component is coupled with the `@sap/site-entry` node module.

**Related Information**  


[Consume SAP Node.js Packages](consume-sap-node-js-packages-ddcff14.md "A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.")

[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[Configuring the HDI Deployer](../040-HANA-Cloud-DB-Dev-Persistence-Model/configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

[Maintaining Multitarget Application Routes and Destinations](../090-HANA-Cloud-DB-Dev-MTA-Routes/maintaining-multitarget-application-routes-and-destinations-0117b71.md "Define application routes and destinations.")

[Bytes Utility](https://www.npmjs.com/package/bytes)

[Application Security Descriptor Configuration Syntax](../100-HANA-Cloud-DB-Dev-Security/application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

