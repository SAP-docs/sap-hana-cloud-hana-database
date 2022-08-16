<!-- loioa4a91b53a407465e8478104af9e40a03 -->

# Multitarget Application Package Descriptor Configuration Syntax

The package descriptor defines the prerequisites and dependencies that apply to packages in a JavaScript multitarget application deployed in the Cloud Foundry run time.



The contents of the multitarget application package descriptor, `package.json`, must be formatted according to the JSON rules. The required syntax for the properties and their corresponding keys is described below:

> ### Sample Code:  
> ```
> {
>   "name": "<application name>",
>   "description": "<application description>",
>   "private": true,
>   "version": "1.3.1",
>   "repository": {
>     "url": "git@github.acme.com:xs-samples/nodejs-hello-world.git"
>   },
>   "dependencies": {
>     "@sap/xsjs": "^1.0.5",
>     "@sap/approuter": "^2.3.1"
>   },
>   "engines": {
>     "node": ">=0.10.x <0.12"
>   },
>   "scripts": {
>     "start": "node --max-old-space-size=400 --expose-gc main.js"
>   }
> }
> 
> ```



<a name="loioa4a91b53a407465e8478104af9e40a03__section_rsm_zxr_xs"/>

## name

The name of the JavaScript application whose package prerequisites and dependencies are defined in this package description.

> ### Sample Code:  
> ```
> "name": "<application name>",
> 
> ```



<a name="loioa4a91b53a407465e8478104af9e40a03__section_y1c_zxr_xs"/>

## description

A short description the JavaScript application whose package prerequisites and dependencies are defined in this package description.

> ### Sample Code:  
> ```
> "description": "<application description>",
> 
> ```



<a name="loioa4a91b53a407465e8478104af9e40a03__section_rnx_b2g_dt"/>

## private

Use the `private` property to indicate if access to the package specified in `name` is restricted. Private packages are not published by `npm`.

> ### Sample Code:  
> ```
> "private": true,
> 
> ```



<a name="loioa4a91b53a407465e8478104af9e40a03__section_gdl_yxr_xs"/>

## version

The version of the JavaScript application whose package prerequisites and dependencies are defined in this package description.

The version value must follow the standard format for semantic versioning: <code><i class="varname">&lt;major&gt;</i>.<i class="varname">&lt;minor&gt;</i>.<i class="varname">&lt;patch&gt;</i></code>. The restriction ensures a reliable contract between a development environment and deployed system components.

> ### Sample Code:  
> ```
>  
> "version": "<Major_Version>.<Minor_Version>.<Patch_Version>" 
> 
> ```

> ### Tip:  
> When defining [`dependencies`](multitarget-application-package-descriptor-configuration-syntax-a4a91b5.md#loioa4a91b53a407465e8478104af9e40a03__section_dtp_vxr_xs) and run-time [`engines`](multitarget-application-package-descriptor-configuration-syntax-a4a91b5.md#loioa4a91b53a407465e8478104af9e40a03__section_ob3_vxr_xs) in the package description, you can specify a range of versions, for example: `>1.0.3`, `<=1.2.5`, `^1.0.5` \(compatible with version 1.0.5\), or `1.2.x` \(any 1.2 version\), or `1.1.0 - 1.3.12` \(any version including or between the specified versions\).



<a name="loioa4a91b53a407465e8478104af9e40a03__section_nbd_xxr_xs"/>

## repository

The absolute path to the repository used by the JavaScript application whose package prerequisites and dependencies are defined in this package description.

> ### Sample Code:  
> ```
> "repository": {
>     "url": "<repository>@<host.name>:</path/to/your/repository>"
> },
> ```

> ### Sample Code:  
> ```
>  "repository": { 
>      "url": "git@github.acme.com:samples/nodejs-hello-world.git" 
>    }, 
> 
> ```



<a name="loioa4a91b53a407465e8478104af9e40a03__section_dtp_vxr_xs"/>

## dependencies

A list of dependencies that apply to the JavaScript application whose package prerequisites and dependencies are defined in this package description.

> ### Sample Code:  
> ```
> "dependencies": {
>     "@sap/xsjs": "^1.2.5",
>     "@sap/approuter": "^2.3.1",
>     "@sap/cds": "^1.1.7",
>     "@sap/xssec": "^1.3.6", 
>     "@sap/xsenv": "^1.2.2"
> },
> ```

> ### Note:  
> In the package description, you can define a range of versions, for example: `>1.0.3`, `<=1.2.5`, or `1.2.x` \(any 1.2 version\), and `1.1.0 - 1.3.12` \(any version including or between the specified versions\).



<a name="loioa4a91b53a407465e8478104af9e40a03__section_ob3_vxr_xs"/>

## engines

The run-time engines used by the application specified in the `name` property.

> ### Sample Code:  
> ```
> "engines": {
>     "node": >=0.10.x <0.12"
> },
> ```

> ### Note:  
> In the package description, you can define one or a range of versions, for example: `>1.0.3`, `<=1.2.5`, or `1.2.x` \(any 1.2 version\), and `1.1.0 - 1.3.12` \(any version including or between the specified versions\).



<a name="loioa4a91b53a407465e8478104af9e40a03__section_drw_5xr_xs"/>

## scripts

The script containing the command used to start the JavaScript application along with any additional \(required\) options and parameters.

> ### Sample Code:  
> ```
> "scripts": {
>     "start": "node --max-old-space-size=400 --expose-gc main.js"
>   },
> ```

**Related Information**  


[Create the Multitarget Application Package Descriptor](create-the-multitarget-application-package-descriptor-0b0ed18.md "The package descriptor defines a JavaScript application's design-time and run-time dependencies in Cloud Foundry.")

