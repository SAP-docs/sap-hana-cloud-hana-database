<!-- loiob2e355a5137c4799932f776716b292c9 -->

# Maintaining the Multitarget Application Development & Deployment Descriptors

Development descriptors are used to generate deployment descriptors, which define the details required at application-deployment time.

The deployment description is contained in the application deployment “descriptor”, which specifies what you want to build \(and how\) as well as where \(and how\) to deploy it, as follows:

**MTA Development and Deployment Descriptors**


<table>
<tr>
<th valign="top">

File Name



</th>
<th valign="top">

Description



</th>
<th valign="top">

SAP Business App Studio



</th>
<th valign="top">

Cloud MTA Build Tool



</th>
<th valign="top">

CF CLI



</th>
</tr>
<tr>
<td valign="top">

 `mta.yaml` 



</td>
<td valign="top">

 **Development** descriptor for a multi-target application \(MTA\). The information in the `mta.yaml` file provides instructions for the MTA development and build process.



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `mtad.yaml` 



</td>
<td valign="top">

 **Deployment** descriptor for a multi-target application \(MTA\). The information in the `mtad.yaml` file provides instructions for the deploy service.



</td>
<td valign="top">

\*



</td>
<td valign="top">

\*



</td>
<td valign="top">

✔



</td>
</tr>
</table>

The information defined in the development descriptor \(`mta.yaml`\) is used by *SAP Business Application Studio* and the Cloud MTA Build Tool \(MBT\) to generate the `mtad.yaml` file that is required to deploy the application to the Cloud Foundry run-time environment. The information in the generated **deployment** descriptor `mtad.yaml` file provides the instructions that are carried out when the application is deployed.

> ### Note:  
> If you use *SAP Business Application Studio* to develop an MTA, both the `mta.yaml` and the `mtad.yaml` are created automatically. The `mta.yaml` is generated when you create the application project, and this is where you specify details of the development and build process. The `mtad.yaml` deployment descriptor is created during the application project's build or deployment process.

MTAs are transported in the form of a compressed and digitally signed archive called an MTA archive or “MTAR”. Deploying an MTA involves the deployment of each application module to its corresponding target run time. The MTA archive \(for example, `myMTAarchive.mtar`\) that is deployed conforms to the standard Java JAR specification. For this reason, an additional file, the `MANIFEST.MF` file, is also required for the deployment operation; the `MANIFEST.MF` contains a list of the files in the MTAR archive to be deployed.

The development and deployment descriptors for an multi-target application must be located in the root folder of the application project, as illustrated \(in **bold text**\) in the following example.



> ### Sample Code:  
> ```
> AppName
> |- db/
> |  |- package.json
> |  \- src/                      
> |- web/
> |  |- package.json
> |  \- resources/                
> |- js/
> |  |- start.js
> |  |- package.json                          
> |  \- src/                      
> |- xs-security.json
> \- mta[d].yaml       # Development [deployment] build manifest *
> 
> ```

> ### Note:  
> \* You only need to concern yourself with the contents of the `mtad.yaml` deployment descriptor if you are using command-line or custom tools; in these cases you must also ensure that the `mtad.yaml` is checked into version control along with the other application-project artifacts. If you are using *SAP Business Application Studio* or the Cloud MBT, the `mtad.yaml` file is generated for you automatically and does not need to be managed with version-control tools.

**Related Information**  


[Create the MTA Description Files](create-the-mta-description-files-ebb42ef.md "Multi-target applications are defined in multiple descriptor files.")

[The MTA Development Descriptor](the-mta-development-descriptor-4486ada.md "Multi-target applications are defined in a design-time development descriptor.")

[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

[The Cloud MTA Build Tool \(MBT\)](the-cloud-mta-build-tool-mbt-1412120.md "A new tool for building deployment archives for multitarget applications (MTA).")

