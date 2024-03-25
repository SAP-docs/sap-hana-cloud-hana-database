<!-- loio63ae89ee80ec4671b551d459e129d4a1 -->

# CANCEL ASYNC CALL Statement

Cancels a running procedure executed with the ASYNC keyword.



<a name="loio63ae89ee80ec4671b551d459e129d4a1__sql_call_1sql_call_syntax"/>

## Syntax

```
CANCEL ASYNC CALL <async_call_id>
```



<a name="loio63ae89ee80ec4671b551d459e129d4a1__sql_call_1sql_call_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<async\_call\_id\>*

</b></dt>
<dd>

Specifies the ID of the procedure executed with the ASYNC keyword being canceled.



</dd>
</dl>



<a name="loio63ae89ee80ec4671b551d459e129d4a1__section_jg2_gyq_11c"/>

## Examples

This example cancels the background execution of the procedure assigned ID 24.

```
CANCEL ASYNC CALL 24;
```

