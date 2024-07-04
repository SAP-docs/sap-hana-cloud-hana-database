<!-- loioc2f1007259654a8f941bab6cebd0ad31 -->

# REFRESH PSE Statement \(System Management\)

Refreshes a managed PSE.



<a name="loioc2f1007259654a8f941bab6cebd0ad31__section_wzq_zvk_y1c"/>

## Syntax

```
REFRESH PSE <managed_pse_name>
```



<a name="loioc2f1007259654a8f941bab6cebd0ad31__section_xzq_zvk_y1c"/>

## Syntax Elements


<dl>
<dt><b>

*<managed\_pse\_name\>*

</b></dt>
<dd>

Specifies the name of the managed PSE.



</dd>
</dl>



<a name="loioc2f1007259654a8f941bab6cebd0ad31__section_jtv_tj3_5rb"/>

## Permissions

You must have the REFERENCES object privilege on the PSE.



<a name="loioc2f1007259654a8f941bab6cebd0ad31__section_n1r_zvk_y1c"/>

## Examples

This example refreshes the managed PSE pse1.

```
REFRESH PSE pse1;
```

**Related Information**  


[ALTER PSE Statement \(System Management\)](alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[CREATE PSE Statement \(System Management\)](create-pse-statement-system-management-4d80bf6.md "Creates a personal security environment (PSE).")

[DROP PSE Statement \(System Management\)](drop-pse-statement-system-management-25d6795.md "Drops a PSE.")

[SET PSE Statement \(System Management\)](set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE, which is the type of trust validation for the PSE to use.")

[UNSET PSE Statement \(System Management\)](unset-pse-statement-system-management-4082553.md "Remove the assigned purpose for a PSE along with any assigned objects.")

[M\_MANAGED\_PSES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-managed-pses-system-view-5c745ca.md "Provides information about managed personal security environments (managed PSEs).")

