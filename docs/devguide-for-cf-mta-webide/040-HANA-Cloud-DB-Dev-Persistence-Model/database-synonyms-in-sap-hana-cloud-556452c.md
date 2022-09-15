<!-- loio556452cac83f423597d3a38a6f225e4b -->

# Database Synonyms in SAP HANA Cloud

You can use synonyms in SAP HANA Cloud to enable access to objects that are not in the same schema or application container.

In general terms a synonym is an alias for a database object. Whenever you use a synonym, it is useful to try to mentally replace it by its base object: the object that is the target of the synonym. A synonym belongs to its own schema, which is typically \(but not always\) independent of the schema to which the target database object belongs. Synonyms can be created for tables, views, procedures, table functions, scalar functions and sequences. Synonyms are most commonly used to hide the real object names from consumers or to give a database object a more convenient name. In migration scenarios, it also sometimes necessary to be able to recreate the synonym after modifying it to point to another target object.

To create a synonym, a user needs the following privileges:

-   `SELECT`

    For the tables, views, and sequences to which the synonym refers as base objects

-   `EXECUTE`

    For procedures and functions to which the synonym refers as base object.


After creation, the synonym exists independently of the base target object. A synonym remains in existence even if its creator no longer has the privilege required to access the synonym's target database object or the base target object has been deleted.

> ### Note:  
> A synonym can be “private” \(belonging to a specific schema\), or “public” \(residing in the special schema `PUBLIC`\).

Although a public synonym can be used by any user without explicitly specifying the schema name, the appropriate privilege for accessing the base object of a public synonym is still required. If public and private objects or synonyms have identical names, the private synonym is used.

> ### Restriction:  
> It is not possible to use a synonym as the base \(target\) object for another synonym.

If you need to point a synonym to another synonym, you have to put a real database object in between the two synonyms. For example, you would need to create a view for a scenario where the second synonym's base object is a table or a table function. If the second synonym points to a procedure, you must insert an additional procedure between the synonyms. If the second synonym points to a scalar function, you must insert an additional scalar function. It is not possible to use a sequence as the base target object for another sequence with a synonym in between.



## Synonyms in SAP HANA Cloud

In HDI, database objects such as tables and views reside in an application-specific HDI container, which is a sort of generated schema. For this reason, development has to be done in a schema-less way. The concept of isolated HDI containers makes it possible to deploy multiple containers into the same system, have multiple developers work on the same application independently from other developers, or even deploy applications and containers into a public Cloud environment, where binding between different containers \(or services in general\) should not be hard coded but done using a configuration mechanism during deployment.

Synonyms play an important role in HDI, where using synonyms is the designated method to enable access to objects in other schemas, for example, a schema owned by another application's HDI container.

The following diagram provides a visual overview of the most commonly used scenarios where synonyms in can be effectively deployed to access objects in classic schemas outside of HDI, for example:

-   Enabling access to tables provided by a classic \(ERP\) schema from an application's schema \(an HDI container\)

-   Enabling access to tables provided by one application schema from a different application schema, for example, one schema containing some data, and different Data Warehouse \(DW\) multitarget applications accessing the data

-   Transporting schemas and the objects they contain to \(and deploying them in\) another environment


![](images/Synonyms_for_Classic_Schema_Access_285289c.png)

In the context of database synonyms, it is important to understand the role of the following users:

-   Schema owner

    The user who owns the HDI container \(or schema\) where the synonym resides

-   Object owner

    The user who creates the objects deployed within the container, for example, the synonym. The synonym's “target” objects belong to another user, for example, the user of the external schema.

-   Application user

    The SAP HANA Cloud run-time user who runs the applications in the HDI container


**Related Information**  


[Using Synonyms to Access External Schemas and Objects](using-synonyms-to-access-external-schemas-and-objects-bdc9f7a.md "Deploy synonyms to enable cross-container access to external objects.")

[Syntax Options in the hdbgrants File](syntax-options-in-the-hdbgrants-file-f49c1f5.md "Assign the privileges required by users to access objects in the target schema.")

