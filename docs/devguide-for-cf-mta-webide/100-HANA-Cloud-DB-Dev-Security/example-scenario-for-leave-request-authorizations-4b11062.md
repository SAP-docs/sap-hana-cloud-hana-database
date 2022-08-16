<!-- loio4b110625a46d4df290009813c309ccfb -->

# Example Scenario for Leave Request Authorizations

You want to create roles and authorizations for the agents in a leave request work flow.

This work flow includes the following agents:

-   Employee

-   Manager \(approver\)

-   Payroll administrator




## Work Flow

The example used here to explain the different authorizations required for the different people in a leave-request scenario assumes the following work-flow:

<a name="loio4b110625a46d4df290009813c309ccfb__table_uq2_x4g_mw"/>Leave-Request Work Flow


<table>
<tr>
<th valign="top">

Step



</th>
<th valign="top">

Action



</th>
<th valign="top">

Role



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Create a leave request



</td>
<td valign="top">

Employee



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Approve a leave request



</td>
<td valign="top">

Manager



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

Calculate available leave reserves



</td>
<td valign="top">

Payroll Administrator



</td>
</tr>
</table>



## Employee Authorizations

The employee John Doe needs the authorizations to enable him to create, edit, view, and delete his own requests for leave. He also needs to be able to delete an approved leave requests, for example, if due to a change of plans he decided to go to work on that day after all.

<a name="loio4b110625a46d4df290009813c309ccfb__table_ymn_fcr_st"/>Employee Authorizations


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Role



</th>
<th valign="top">

Authorization



</th>
<th valign="top">

Attribute



</th>
</tr>
<tr>
<td valign="top" rowspan="4">

John Doe



</td>
<td valign="top" rowspan="4">

Employee



</td>
<td valign="top">

Create



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Edit



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

View



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Delete



</td>
<td valign="top">

Own



</td>
</tr>
</table>



## Manager Authorizations

John Doe's manager, Julia Moore, needs the authorizations that enable her to approve John’s leave requests and edit them; she cannot, however, delete them. In addition, she needs the authorization that allows her \(as a manager\) to view, approve, and edit the leave requests of all employees in her department. Since she is also an employee, she needs to be able to create, view, edit, and delete her own leave requests.

<a name="loio4b110625a46d4df290009813c309ccfb__table_w4c_zdr_st"/>Manager \(Approver\) Authorizations


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Role



</th>
<th valign="top">

Authorization



</th>
<th valign="top">

Attribute



</th>
</tr>
<tr>
<td valign="top" rowspan="7">

Julia Moore



</td>
<td valign="top" rowspan="4">

Employee



</td>
<td valign="top">

Create



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Edit



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

View



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Delete



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Manager



</td>
<td valign="top">

Approve



</td>
<td valign="top">

Managed employees



</td>
</tr>
<tr>
<td valign="top">

Edit



</td>
<td valign="top">

Managed employees



</td>
</tr>
<tr>
<td valign="top">

View



</td>
<td valign="top">

Managed employees



</td>
</tr>
</table>



## Payroll Administrator Authorizations

A payroll administrators of the human resources department is only interested in viewing all approved leave requests. He needs the total number of approved leave request and of days off so that he can feed them into the payroll system, which will calculate the leave reserve. He is not involved in any way in the approval process. Since the payroll administrator, Mark Smith, is an employee as well, he also needs the authorization to create, view, edit, and delete his own leave requests.

<a name="loio4b110625a46d4df290009813c309ccfb__table_fs1_3pw_st"/>Payroll Administrator Authorizations


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Role



</th>
<th valign="top">

Authorization



</th>
<th valign="top">

Attribute



</th>
</tr>
<tr>
<td valign="top" rowspan="5">

Mark Smith



</td>
<td valign="top" rowspan="4">

Employee



</td>
<td valign="top">

Create



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Edit



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

View



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Delete



</td>
<td valign="top">

Own



</td>
</tr>
<tr>
<td valign="top">

Payroll Administrator



</td>
<td valign="top">

View



</td>
<td valign="top">

All employees



</td>
</tr>
</table>



As we can see, even a simple example such as the one described here involves a number of different authorizations defined in the corresponding attributes. However, the case could be extended further, for example, to enable the manager to view the leave of employees in related departments. With this additional authorization, the manager can see who is available as a substitute for the employees during their respective vacation.

An administrator in the multitarget application can use role templates, scopes, and attributes to shape the roles so that they match the needs and requirements of your organization.

**Related Information**  


[Maintaining Application Security in Cloud Foundry on SAP BTP](maintaining-application-security-in-cloud-foundry-on-sap-btp-35d910e.md "Set up the security components required in the context of multitarget applications on SAP BTP .")

[Building an Authorization Concept for Users of an Application Instance](building-an-authorization-concept-for-users-of-an-application-instance-0dd773f.md "Business users in an SAP HANA multitarget application should have different authorizations because they work in different jobs.")

