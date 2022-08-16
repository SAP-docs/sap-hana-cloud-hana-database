<!-- loioa79f968da160451d95f71dc18e3e61f3 -->

# The MANIFEST.MF File

The `MANIFEST.MF` file contains a list of the files in the standard Jar archive.

In the context of the SAP HANA MTA archive, the \(`manifest.mf`\) file contains the usual elements of the standard JAR manifest file plus a `Name` section for the deployment descriptor \(`mtad.yaml`\). For each MTA module, the `name` section links the module file \(or directory name\) to the corresponding MTA module name in the deployment descriptor. In the following example of a simple `manifest.mf` file one of the modules \(`utils`\) is a directory; the other two \(`runner.war` and `builder.war`\) are single files.

> ### Sample Code:  
> ```
> Manifest-Version: 1.0
> Trusted-Library: true
> Created-By: Apache Maven 3.2.5
> Build-Jdk: 1.8.0_11
>  
> Name: META-INF/mtad.yaml
> Content-Type: text/plain
>   
> Name: devx/runner.war
> MTA-module: di-runner
> Content-Type: application/war
>   
> Name: devx/utils
> MTA-module: di-utils
> Content-Type: content-type text/directory
>   
> Name: devx-di/builder.war
> MTA-module: di-builder
> Content-Type: application/war
> 
> ```

The manifest file may also contain other standard jar-file information, for example, hash values and security signatures.

> ### Note:  
> If the modules specified in the corresponding deployment description file \(`mtad.yaml`\) contain a `path` attribute, its value must be identical to the `Name` information in the `MANIFEST.MF` file.

**Related Information**  


[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

