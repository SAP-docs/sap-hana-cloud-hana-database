<!-- loio0e96265f0e6a453896bcd4d9038f3661 -->

# Security Considerations

An overview of the best practices that need to be implemented for secure development.



<a name="loio0e96265f0e6a453896bcd4d9038f3661__section_nn2_2xy_mpb"/>

## Cloud Foundry Credentials

The Cloud Foundry development model uses services to pass information to applications. The SAP HANA editors use a similar mechanism to access run-time data in the SAP HANA database, for example, to provide dynamic functionality such as auto-completion or the integration of external objects into a development project. To make use of this dynamic functionality the SAP HANA editors must be able to access a Cloud Foundry run-time environment, which is is performed by means of the Cloud Foundry's command-line interface \(CLI\). Before interacting with Cloud Foundry, a user must log on by using a Cloud Foundry API end point. After logon, a user token is stored by the Cloud Foundry CLI in the user's home directory in a file named `config.json`. It is essential to ensure that this file is protected from unauthorized access.



<a name="loio0e96265f0e6a453896bcd4d9038f3661__section_tl5_fxy_mpb"/>

## SAP HANA Credentials

When a SAP HANA database module is bound to a Cloud Foundry service, the credentials contained in one of the service's service key are copied to a local file named `.env`, which is located in the database module's root directory. The credentials are, among others, the host and port of the SAP HANA database, as well as the user names and passwords of technical users that can access the HDI container backing the Cloud Foundry service.

> ### Tip:  
> For details about which privileges these users can have, see *Configuring the HDI Deployer* in *Related Information* below.

Since the `.env` files can contain sensitive information, users must ensure that these files are protected from unauthorized access. By default, the permissions of the `.env` file are set to allow access only for the user who created the file. In addition, To prevent the accidental publication of the database credentials to a Git repository, the `.env` files are added to the `.gitignore` file that is automatically generated with a database module. f a different version control system is used, the appropriate measures must be taken to prevent `.env` files from being added to the version-control repository.

> ### Note:  
> The *SAP HANA Projects* explorer checks if an application project's `.gitignore` file includes an entry for the application's `.env` file. If no entry for `.env` exists, a warning is displayed with a recommendation to add the `.env` file to the list of files for Git to ignore.



<a name="loio0e96265f0e6a453896bcd4d9038f3661__section_wv4_gxy_mpb"/>

## SAP Business Application Studio Extensions

SAP Business Application Studio allows the installation of arbitrary Visual Studio Code extensions. These extensions have very few limitations in the IDE and can access all data available in a workspace. It is important to bear in minde that malicious extensions can steal or manipulate any data that are accessible in the workspace. For this reason, users must ensure that only trusted extensions are installed in an SAP Business Application Studio development space \(dev space\).

**Related Information**  


[Configuring the HDI Deployer](../40-HANA-Cloud-DB-Dev-Persistence-Model/configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

