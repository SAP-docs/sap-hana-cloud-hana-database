<!-- loio00340d4ede0a43ceb0a67f36bbc46a3a -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create Virtual Tables

Virtual tables enable you to access objects in other databases without having to replicate in SAP HANA.



<a name="loio00340d4ede0a43ceb0a67f36bbc46a3a__prereq_qrw_sym_bhb"/>

## Prerequisites

You must already have created a remote source.



## Context

SAP Business Application Studio supports the creation of virtual tables using either a code editor or a built-in Wizard. The Wizard is designed to help those users who are not sure of the syntax required to create virtual tables in the code editor. After creating the virtual tables, you can use them as a data source.



## Procedure

1.  Start SAP Business Application Studio.

2.  Select the *SAP HANA Database Module* in which you want to create the calculation view.

3.  In the *Workspace* view, select the *src*folder.

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Choose *View* \> *Find Command...*

    2.  Locate and run the command *SAP HANA: Create HDB Virtual Table*.

        In the command palette, type ***virtual*** and choose *SAP HANA: Create HDB Virtual Table* in the list of commands displayed.


4.  Select the remote source and click *Next*.

5.  Use the filter parameters to search for one or more remote objects you want to create a virtual table from and click *Next*.

6.  Enter a name for the virtual object and click *Finish*.

    Use the naming format ***namespace::virtual\_table\_name***.

7.  Choose *Save* in the menu bar or  [CTRL\] + [S\] to save your file \(virtual table\).

8.  Buildand deploy an SAP HANA database module.

    The build process uses the design-time database artifacts to generate the corresponding actual objects \(run-time objects\) in the HDI container.

    1.  In the *SAP HANA PROJECTS* explorer, select the application project whose database artifacts you want to deploy, and choose <span class="FPA-icons"></span> \(Deploy\).



