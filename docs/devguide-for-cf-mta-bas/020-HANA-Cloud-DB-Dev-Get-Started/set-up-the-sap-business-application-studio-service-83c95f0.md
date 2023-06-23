<!-- loio83c95f0e0f754bda86e75feafc1e3131 -->

# Set up the SAP Business Application Studio Service

Subscribe to the SAP Business Application Studio Cloud service.



<a name="loio83c95f0e0f754bda86e75feafc1e3131__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You have access to the SAP BTP cockpit.
-   You have an enterprise account on the SAP BTP \(for which you have administrator rights\).
-   You have created a subaccount in Cloud Foundry \(for which you have administrator rights\)
-   The subaccount is entitled to use the SAP Business Application Studio



## Context

SAP Business Application Studio is a new SAP service in Cloud Foundry which offers a modular development environment tailored for the development of business applications for the SAP HANA. Before you can start using SAP Business Application Studio, you need to subscribe to the Cloud application service, start the service, create a development space, and connect the development space to the Cloud Foundry run-time environment.

> ### Note:  
> SAP Business Application Studio needs to connect to the SAP HANA Cloud instance where you want to deploy your application’s database artifacts. By default, SAP HANA Cloud accepts all connections from allowed IP addresses in SAP BTP, for example, in the same region and infrastructure where SAP HANA was provisioned.
> 
> If you are having problems connecting the SAP Business Application Studio service to your SAP HANA Cloud instance, you can use SAP BTP cockpit to configure SAP HANA Cloud to allow connections from additional IP addresses, for example, the ones hosting SAP Business Application Studio for your Cloud region and the underlying platform. For more information, see *Related Information* below.

This tutorial shows how to set up and use an instance of the SAP Business Application Studio service, which you can then use to develop and deploy SAP HANA database applications.

> ### Note:  
> This tutorial describes how to enable a service in an SAP BTP **enterprise** account; if you have a **trial** account, the initial steps might differ from those described here. For example, in a trial account you might have to navigate to the subaccount where you want to enable a service.



## Procedure

1.  Start SAP BTP cockpit.

2.  Log into your SAP BTP enterprise account.

3.  Navigate to the subaccount where you want to enable SAP Business Application Studio.

4.  Check your subaccount's subscriptions.

    In the navigation pane of your subaccount, choose *Subscriptions* and check the list of applications to which the subaccount is subscribed.

    > ### Note:  
    > Subscriptions can differ according to Cloud region and infrastructure. See *Related Information* below for some alternative methods to enable access to SAP Business Application Studio.

5.  Subscribe to the SAP Business Application Studio service.

    1.  Search for the SAP Business Application Studio service.

        Type ***studio*** in the search box and choose *Business Application Studio* or, alternatively, click the *Business Application Studio* tile in the list of services.

    2.  Choose *Subscribe* and then *Go to Application*.


6.  Open SAP Business Application Studio.

    On startup, SAP Business Application Studio displays a list of development spaces that are available. If none exists, you must create one, as described in the next tutorial *Set up a Development Space for SAP Business Studio* in *Related Information* below.


**Related Information**  


[Subscribe to SAP Business Application Studio \(AWS and Azure\)](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/19611ddbe82f4bf2b493283e0ed602e5.html)

[Subscribe to SAP Business Application Studio \(China Shanghai\)](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/b53e2618988d4fe99e459d738d2d9960.html)

[Getting Started with SAP Business Application Studio \(Trial Accounts\)](https://help.sap.com/viewer/DRAFT/daa8adb7947848d8af8fc62e838e830e/DEV2/en-US/48ed55ec07e04a02b2218236c336321b.html)

[Set up a Development Space for SAP Business Application Studio](set-up-a-development-space-for-sap-business-application-studio-6697174.md "Create a development space that includes tools that enable application development.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[Troubleshooting Connectivity \(SAP Business Application Studio\)](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/d2005922d0854834b5bbdfb8b9c693cd.html)

[Service Availability by IP Address \(SAP Business Application Studio\)](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/8509485251814213876223e332bfdcbb.html)

[Change Allowed Connections \(SAP HANA Cloud cockpit\)](https://help.sap.com/viewer/db19c7071e5f4101837e23f06e576495/2020_04_QRC/en-US/770d34deb86d4eb49dc944ce9921228c.html)

