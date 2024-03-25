<!-- loio81e15837ac7249938e05e346c391ead5 -->

# REFRESH VIEW Statement \(Data Definition\)

Refreshes an anonymized view.



<a name="loio81e15837ac7249938e05e346c391ead5__section_twq_nnw_sfb"/>

## Syntax

```
REFRESH VIEW <anonymized_view_name> ANONYMIZATION
```



<a name="loio81e15837ac7249938e05e346c391ead5__section_efr_nnw_sfb"/>

## Syntax Elements


<dl>
<dt><b>

*<anonymized\_view\_name\>*

</b></dt>
<dd>

Specifies the name of the anonymized view to refresh.



</dd>
</dl>



<a name="loio81e15837ac7249938e05e346c391ead5__section_zmr_nnw_sfb"/>

## Description

You must refresh a view before you can select from it.

Refreshing a view can fail if privacy constraints cannot be satisfied due to the source data and parameters of the view. If this occurs, you can alter the view to adjust the constraints.

For more information on data anonymization, see the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



<a name="loio81e15837ac7249938e05e346c391ead5__section_cl4_mtb_vfb"/>

## Example

The following example refreshes a fictitious anonymized view called `Illness_K_Anon`:

```
REFRESH VIEW Illness_K_Anon ANONYMIZATION;
```

For a working example of how to refresh an anonymized view, see the anonymized view example found in the Examples section of the CREATE VIEW statement topic.

**Related Information**  


[CREATE VIEW Statement \(Data Definition\)](create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[ANONYMIZATION\_VIEWS System View](../../020-System-Views-Reference/021-System-Views/anonymization-views-system-view-2992220.md "Provides information about anonymized views in the SAP HANA database.")

[ANONYMIZATION\_VIEW\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/anonymization-view-columns-system-view-ee12fae.md "Provides information about the anonymized columns in SAP HANA database.")

[M\_ANONYMIZATION\_VIEWS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-anonymization-views-system-view-6a44772.md "Provides runtime information about anonymized views.")

[Data Anonymization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/6cf9d55f4d3d45b0bcdb41756d86629f.html "Anonymization methods available in the SAP HANA Cloud, SAP HANA database allow you to gain statistically valid insights from your data while protecting the privacy of individuals.") :arrow_upper_right:

