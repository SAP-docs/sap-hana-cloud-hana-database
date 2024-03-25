<!-- loio8732609bd5314b51a17d6a3cc09110c3 -->

# Standard Python Packages for Cloud Foundry

A list of Python packages developed by SAP, which are available for download and use from the Python Package Index \(PyPI\).



SAP provides a selection of Python packages, which are available for download and use from the Python Package Index \(PyPI\). Newer client packages might require a more recent version of Python. For more information, see the following table or *Related Information* below.

The following table lists the SAP Python packages that are currently available. For more details about the contents of each SAP Python package as well as any configuration tips, see the related section below or the `README` file in the corresponding package.

**SAP Python Packages**


<table>
<tr>
<th valign="top">

PyPI Package

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[`sap-instance-manager`](https://pypi.org/project/sap-instance-manager/) 

</td>
<td valign="top">

Python package for creating and deleting service instances per tenant within an application at run time

</td>
</tr>
<tr>
<td valign="top">

[`sap-xssec`](https://pypi.org/project/sap-xssec/) 

</td>
<td valign="top">

Container Security API for Python

</td>
</tr>
<tr>
<td valign="top">

[`sap-cf-logging`](https://pypi.org/project/sap-cf-logging/) 

</td>
<td valign="top">

This is a collection of support libraries for Python applications running on Cloud Foundry provide the following features:

-   Generate structured application log messages
-   Enable web applications in your application stack to collect request metrics

> ### Note:  
> `sap-cf-logging` is an open-source library that is developed by SAP and published on the Python Package Index \(PyPI\).



</td>
</tr>
<tr>
<td valign="top">

[hdbcli](https://pypi.org/project/hdbcli/) 

</td>
<td valign="top">

The SAP HANA Cloud database client provides tools that enable connections to the SAP HANA Cloud database. archive; it is an open-source library that is developed by SAP and published on the Python Package Index \(PyPI\).

</td>
</tr>
</table>



<a name="loio8732609bd5314b51a17d6a3cc09110c3__section_vpc_qrj_ycb"/>

## `sap_instance_manager`

archive; it is an open-source library that is developed byThis package provides a client for the Instance Manager - a component that creates and deletes service instances \(via REST API\) for a specified service key. The Instance Manager can be used in the context of multi-tenant applications, where the tenant ID is the key that an instance is associated with. Python application can dynamically create and delete service instances per tenant at run time. An instance of a managed service of the desired type is created first and is then bound to the application. For an SAP HANA database the managed service is called *managed-hana*. This service binding only provides parameters \(HTTP endpoints and credentials\) which can later be used by the application for creating and deleting service instances of the desired type for each tenant.



### Application Programing Interface \(API\)

The following example shows how to use the instance manager API to manage service instances for an application used by multiple tenants:

> ### Sample Code:  
> Service - Instance Manager API
> 
> ```
> from sap import instance_manager
> 
> # create instance manager client
> client = instance_manager.create(options)
> 
> # create instance
> instance = client.create('my-tenant')
> print(instance)
> # ...
> 
> # get already created instance
> instance = client.get('my-tenant')
> print(instance)
> # ...
> 
> # delete instance
> client.delete('my-tenant')
> ```



### Options

The managed service bound to the application \(for example `managed-hana`\) provides credentials as well as REST endpoints of the Instance Manager - the component that handles creation and deletion of services. These credentials and endpoints are mandatory.

The create and delete operations are executed asynchronously on server side. To provide an easier interface, this library also implements polling until an operation is finished. Developers can tune polling via some optional properties.

Since operations involve network activity \(thus, can be considered relatively slower\) the package also caches the created instances. Cache options can also be provided by developers.

**Instance Manager Configuration Options**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Mandatory

</th>
<th valign="top">

Type

</th>
<th valign="top">

Details

</th>
</tr>
<tr>
<td valign="top">

user

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

User for authentication.

</td>
</tr>
<tr>
<td valign="top">

password

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Password for the user.

</td>
</tr>
<tr>
<td valign="top">

post\_managed\_instance\_url

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

REST endpoint used for creating a new service instance for a tenant.

</td>
</tr>
<tr>
<td valign="top">

get\_managed\_instance\_url

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

REST endpoint.

</td>
</tr>
<tr>
<td valign="top">

get\_all\_managed\_instances\_url

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

REST endpoint used for getting details about all instances \(for all tenants\).

</td>
</tr>
<tr>
<td valign="top">

delete\_managed\_instance\_url

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

REST endpoint used for deletion of a service instance.

</td>
</tr>
<tr>
<td valign="top">

polling\_interval\_millis

</td>
<td valign="top">

No

</td>
<td valign="top">

integer

</td>
<td valign="top">

States how many milliseconds to wait between requests in the polling phase. Defaults to 300 milliseconds. Minimum value is 0.

</td>
</tr>
<tr>
<td valign="top">

polling\_timeout\_seconds

</td>
<td valign="top">

No

</td>
<td valign="top">

integer

</td>
<td valign="top">

Sets a limit for the amount of time \(in seconds\) that can be spent in polling. Defaults to 120 seconds. Minimum value is 1.

</td>
</tr>
<tr>
<td valign="top">

cache\_max\_items

</td>
<td valign="top">

No

</td>
<td valign="top">

integer

</td>
<td valign="top">

States the capacity of the cache. Default value is 500. Minimum value is 1.

</td>
</tr>
<tr>
<td valign="top">

cache\_item\_expire\_seconds

</td>
<td valign="top">

No

</td>
<td valign="top">

integer

</td>
<td valign="top">

Number of seconds after which a cache entry expires. Defaults to 600 seconds. Minimum value is 1.

</td>
</tr>
</table>

> ### Note:  
> A managed service binding contains all of the mandatory properties mentioned above.

> ### Note:  
> It is recommended to have a single instance manager client Python object per managed service bound to the application.



### Methods

The following table lists the methods available with the instance-manager API:

**Instance-Manager API Methods**


<table>
<tr>
<th valign="top">

Method

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`create(tenant, optional_parameters)` 

</td>
<td valign="top">

Creates a service instance for the provided tenant. The method polls until the instance is successfully createdk. Reports error if an instance for this tenant already exists. The second argument is optional.

</td>
</tr>
<tr>
<td valign="top">

`get(tenant)` 

</td>
<td valign="top">

Retrieves the corresponding service instance for the specified tenant either from the cache or from the server. A returned value of `None` indicates that no service instance exists for the specified tenant.

> ### Restriction:  
> The `get` method only polls if the service instance is in status `CREATION_IN_PROGRESS`. In all other cases it returns the service instance as it is on server. There is no guarantee that the `credentials` property on the `instance` object is included in the callback.



</td>
</tr>
<tr>
<td valign="top">

`get_all()` 

</td>
<td valign="top">

Retrieves the service instances for all tenants as an array of objects. Filtering of the instances according to their status \(e.g. `CREATION_SUCCEEDED`, `CREATION_IN_PROGRESS`\) does not take place. Thus, having the credentials property on each of the instances provided is not guaranteed. This method updates the cache.

</td>
</tr>
<tr>
<td valign="top">

`delete` 

</td>
<td valign="top">

Removes the service instance for the provided tenant. The method polls until the instance is successfully deleted and then invokes the callback. An error is reported if no instance exists for the specified tenant.

</td>
</tr>
</table>

> ### Tip:  
> If the callback of a method is invoked with an error and the error is caused by an unexpected HTTP response code received from the server, then the error object will have a `statusCode` property with the same status code as the received HTTP response.



<a name="loio8732609bd5314b51a17d6a3cc09110c3__section_atx_2vt_vt"/>

## sap\_xssec

The client security library includes the HDI container security API for Python.

Authentication for Python SAP HANA applications relies on a special usage of the OAuth 2.0 protocol, which is based on central authentication at the SAP HANA User Authentication & Authorization \(UAA\) server that then vouches for the authenticated user's identity by means of a so-called OAuth Access Token. The current implementation uses as access token a JSON web token \(JWT\), which is a signed text-based token formatted according to the JSON syntax.

In a typical deployment scenario, your Python application will consist of several parts, which appear as separate application packages in your manifest file, for example:

-   Database artifacts

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/db/</code>\) describes and defines the SAP HANA database content

-   Application logic

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/py/</code>\) contains the application logic: code written in Python. This module can make use of this application-container security API for Python.

-   UI client

    This application module \(<code><i class="varname">&lt;myAppName&gt;</i>/web/</code>\) is responsible for the UI layer; this module can make use of the application router functionality \(defined in the file `xs-app.json`\).


> ### Note:  
> The application logic written in Python and the application router should be bound to one and the same UAA service instance so that these two parts use the same OAuth client credentials.

To use the capabilities of the application-container security API, add the package “`sap_xssec`” to the dependencies section of your application's `package.json` file. To enable tracing, set the environment variable `DEBUG` as follows: `DEBUG=xssec:*`.



### Usage

To use the container security API, it is necessary to provide a JWT token. The examples below rely on users and credentials that you should substitute with the ones in your context. The typical use case for calling this API lies from within a container when an HTTP request is received. The authorization header \(with keyword “`bearer`” \) already contains an access token; you can remove the prefix bearer and pass the remaining string to the API as “`access_token`”, as illustrated in the following example:

> ### Sample Code:  
> ```
> from sap import xssec
> from cfenv import AppEnv
> 
> env = AppEnv()
> uaa_service = env.get_service(name='<uaa_service_name>').credentials
> 
> security_context = xssec.create_security_context(access_token, uaa_service)
> ```

The example above uses the Python module `cfenv` to retrieve the configuration of the UAA service instance.

The creation function `xssec.create_security_context` is used for an end-user token \(for example, with “grant\_type” `password` or `authorization_code`\) where user information is expected to be available within the token and, as a consequence, within the security context. `create_security_context` also accepts a token of grant type `client_credentials`, which enables the creation of a limited security context where certain functions are not available, as described in more detail in the Security API documentation below.



### Container Security API

The complete details of the application-container security API including all parameters and options are available in the README file included in the `sap_xssec` package.

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

`create_security_context` 

</td>
<td valign="top">

Creates the “security context” by validating the received access token against credentials put into the application's environment via the UAA service binding

</td>
</tr>
<tr>
<td valign="top">

`get_logon_name` 

</td>
<td valign="top">

Returns the user's logon name \*

</td>
</tr>
<tr>
<td valign="top">

`get_given_name` 

</td>
<td valign="top">

Returns the user's given \(first\) name \*

</td>
</tr>
<tr>
<td valign="top">

`get_family_name` 

</td>
<td valign="top">

Returns the user's family name \*

</td>
</tr>
<tr>
<td valign="top">

`get_email` 

</td>
<td valign="top">

Returns the user's email address \*

</td>
</tr>
<tr>
<td valign="top">

`get_origin` 

</td>
<td valign="top">

Returns the user origin. The origin is an alias that refers to a user store in which the user is persisted. For example, users that are authenticated by the User Account and Authentication \(UAA\) service itself \(with a combination of user name and password\) have their origin set to the value "uaa".

</td>
</tr>
<tr>
<td valign="top">

`check_local_scope` 

</td>
<td valign="top">

Checks a scope that is published by the current application in the `xs-security.json` file. Returns “True” if the checked scope is included in the user's authorization scopes \(otherwise “False”\)

</td>
</tr>
<tr>
<td valign="top">

`check_scope` 

</td>
<td valign="top">

Checks a scope that is published by an application. Returns “True” if the checked scope is included in the user's authorization scopes \(otherwise “False”\)

</td>
</tr>
<tr>
<td valign="top">

`get_token` 

</td>
<td valign="top">

Returns a token that can be used to connect to the SAP HANA database. If the token that the security context has been instantiated with is a foreign token \(meaning that the OAuth client contained in the token and the OAuth client of the current application do not match\), “`None`” is returned instead of a token.

</td>
</tr>
<tr>
<td valign="top">

`get_hdb_token` 

</td>
<td valign="top">

Returns a token that can be used to connect to the SAP HANA database. If the token that the security context has been instantiated with is a “foreign” token \(the OAuth client contained in the token and the OAuth client of the current application do not match\), “`None`” is returned instead of a token.

</td>
</tr>
<tr>
<td valign="top">

`request_token_for_client` 

</td>
<td valign="top">

Requests a token with `grant_type=user_token` from another client. The requesting client must also have `grant_type=user_token`, and the current user token must include the authorization scope `uaa.user`.

</td>
</tr>
<tr>
<td valign="top">

`request_token_for_client_async` 

</td>
<td valign="top">

This method provides the same functionality as `request_token_for_client` above, but with added support for asynchronous frameworks, for example, *django* and *fastAPI*.

</td>
</tr>
<tr>
<td valign="top">

`has_attributes` 

</td>
<td valign="top">

Returns “`True`” if the token contains any user attributes; otherwise “`False`”.

</td>
</tr>
<tr>
<td valign="top">

`get_attribute` 

</td>
<td valign="top">

Returns the attribute exactly as it is contained in the access token. If no attribute with the given name is contained in the access token, “`None`” is returned. If the token that the security context has been instantiated with is a foreign token \(the OAuth client contained in the token and the OAuth client of the current application do not match\), “`None`” is returned regardless of whether the requested attribute is contained in the token or not.

</td>
</tr>
<tr>
<td valign="top">

`get_additional_auth_attr` 

</td>
<td valign="top">

Requires the `name` of the additional authentication attribute requested. Returns the requested attribute exactly as it is contained in the access token. If no attribute with the given `name` is contained in the access token, `None` is returned.

</td>
</tr>
<tr>
<td valign="top">

`is_in_foreign_mode` 

</td>
<td valign="top">

Returns “`True`” if the token, that the security context has been instantiated with, is a foreign token that was not originally issued for the current application, otherwise “`False`”.

</td>
</tr>
<tr>
<td valign="top">

`get_subdomain` 

</td>
<td valign="top">

Returns the subdomain that the access token has been issued for.

</td>
</tr>
<tr>
<td valign="top">

`get_clientid` 

</td>
<td valign="top">

Returns the client id that the access token has been issued for.

</td>
</tr>
<tr>
<td valign="top">

`get_identity_zone` 

</td>
<td valign="top">

Returns the identity zone that the access token has been issued for

</td>
</tr>
<tr>
<td valign="top">

`get_subaccount_id` 

</td>
<td valign="top">

Returns the subaccount ID that the access token has been issued for

</td>
</tr>
<tr>
<td valign="top">

`get_expiration_date` 

</td>
<td valign="top">

Returns the expiration date of the access token as a Javascript “Date” object

</td>
</tr>
<tr>
<td valign="top">

`get_clone_service_instance_id` 

</td>
<td valign="top">

Returns the id of the cloned service instance, if the XSUAA broker plan is used

</td>
</tr>
<tr>
<td valign="top">

`get_grant_type` 

</td>
<td valign="top">

Returns the grant type of the JWT token, for example: `authorization_code`, `password`, `client_credentials`, etc.

</td>
</tr>
</table>

> ### Note:  
> \* Not available for tokens of grant type `client_credentials`



<a name="loio8732609bd5314b51a17d6a3cc09110c3__section_dhv_x21_cdb"/>

## sap\_cf\_logging

This is a lightweight library for Python applications that is compatible with the Python logging module, emits JSON log and supports request instrumentation.



### Installation

> ### Note:  
> `sap_cf_logging` is an open-source library that is developed by SAP and published on the Python Package Index \(Pypi\). To install “`sap_cf_logging`”, you must use the standard Python tools.

To install the packages run the following command in your command line interface:

```
pip install sap_cf_logging
```



### Usage

To set up your application, the logging library needs to be initialized. Depending on you application type, different initialization is used. You should usually do this in your application entrypoint.

For CLI applications you just need to call `cf_logging.init()` once to configure the library. The library will try to configure future loggers to emit logs in JSON format.

After installation is complete you need to perform the following actions:

1.  Import the `cf_logging` library and set up Flask logging on the application.

    > ### Sample Code:  
    > Flask
    > 
    > ```
    > from sap.cf_logging import flask_logging
    > 
    > app = flask.Flask(__name__)
    > flask_logging.init(app, logging.INFO)
    > ```

2.  Use Python's logging library.

    > ### Sample Code:  
    > ```
    > @app.route('/')
    > def root_route():
    >     logger = logging.getLogger('my.logger')
    >     logger.info('Hi')
    > 
    >     return 'ok'
    > ```

3.  Note the logs generated by the application.

4.  Set up Sanic on the application.

    > ### Sample Code:  
    > ```
    > import sanic
    > import logging
    > 
    > from sanic.response import HTTPResponse
    > from sap.cf_logging import sanic_logging
    > from sap.cf_logging.core.constants import REQUEST_KEY,
    > 
    > app = sanic.Sanic('test.cf_logging')
    > sanic_logging.init(app)
    > 
    > @app.route('/')
    > async def two(request):
    >     extra = {REQUEST_KEY: request}
    >     logging.getLogger('my.logger').debug('Hi', extra = extra)
    >     return HTTPResponse(body='ok')
    > ```

    > ### Note:  
    > With Sanic you need to pass the request with an extra parameter in the logging API. This is necessary to obtain the *correlation\_id* generated at the beginning of the request or fetched from the HTTP headers.




<a name="loio8732609bd5314b51a17d6a3cc09110c3__section_jcs_5rf_2db"/>

## hdbcli

The library implements PEP 249 - The Python Database API Specification v2.0. For more information about connecting to the SAP HANA database with hdbcli, see *hdbcli* in the *Related Information* below.

**Related Information**  


[hdbcli](https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.02/en-US/f3b8fabf34324302b123297cdbe710f0.html)

[The Python Package Index \(PyPI\)](https://pypi.org/search/?q=sap_instance_manager)

