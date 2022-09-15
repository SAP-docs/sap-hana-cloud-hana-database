<!-- loioa9ed392d27c847caa734ffca8c31e7d4 -->

# Audit Log Services

Retrieve and view audit-logs in the Cloud Foundry run-time environment on SAP BTP.

The SAP Audit Log service is a platform service that stores all the audit logs written on your behalf by other platform services that you use. It allows you to retrieve the audit logs for your SAP BTP subaccount by using the audit-log retrieval API or view the audit logs with the SAP Audit Log Viewer service for SAP BTP.

The SAP Audit Log service provides predefined audit categories for audit logs, for example:

-   Security events

-   Data access events

-   Configuration change events


> ### Note:  
> For more information about how to retrieve and view audit logs for your subaccount, see *Related Information* below.



<a name="loioa9ed392d27c847caa734ffca8c31e7d4__section_bpw_y5t_cz"/>

## Audit Log Retrieval

The audit log retrieval API allows you to retrieve the audit logs for your Cloud Foundry environment account on SAP BTP and display the audit log results as a collection of JSON entities. The audit log retrieval API is protected by OAuth; to call the API, a valid OAuth client must be generated and used by the client system. The retrieval of audit logs with the SAP Audit Log Retrieval API is limited to the size of the audit logs generated for the account.

It is necessary to create an instance of the `auditlog-management` service, for which a service key is also required. The service key contains information \(for example, URL and client credentials\) that is required to generate the OAuth access token, which is used to grant access to the audit logs of the subaccount in the landscape where the service instance is created.



<a name="loioa9ed392d27c847caa734ffca8c31e7d4__section_osc_pwt_cz"/>

## Audit Log Retention

The audit log data stored for your account will be retained for thirty \(30\) days, after which it will be deleted. If you want to retain and use the data longer than 30 days, you can retrieve it by means of the SAP Audit Log Retrieval API for the Cloud Foundry Environment and store it somewhere else.



<a name="loioa9ed392d27c847caa734ffca8c31e7d4__section_nfl_st2_3nb"/>

## Audit Log Viewer

To view the audit logs collected for your Cloud Foundry account, you can use the SAP Audit Log Viewer. Access to the SAP Audit Log Viewer is restricted to users who have subscribed to the SAP Audit Log Viewer service for SAP BTP.

> ### Note:  
> Additional authorization is required to retrieve audit logs for a subaccount. The person viewing the audit logs must be assigned a role collection with the following roles: `auditlog-viewer!t*/Auditlog Auditor` and `auditlog-management!b*/Auditlog Auditor`.

**Related Information**  


[Service Plans and Resources](service-plans-and-resources-0393ce3.md "A service plan is a particular type of service (for example, a database configuration) that is available for use.")

[Auditing](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2022_3_QRC/en-US/ddcb6ed2bb5710148183db80e4aca49b.html "Auditing allows you to monitor and record selected actions performed in the SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

[Audit Logs in the SAP BTP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

