<!-- loio1f935a3dff744f7bbf488271a6c869f4 -->

# DROP PUBLIC KEY Statement \(System Management\)

Drops a public key from the list of keys. The key cannot be dropped if it is used in a PSE store.



<a name="loio1f935a3dff744f7bbf488271a6c869f4__section_rgy_xn5_4pb"/>

## Syntax

```
DROP PUBLIC KEY  <public_key_name>
```



<a name="loio1f935a3dff744f7bbf488271a6c869f4__section_sgy_xn5_4pb"/>

## Syntax Elements


<dl>
<dt><b>

*<public\_key\_name\>*

</b></dt>
<dd>

Specifies the name of the public key to drop.

```
<public_key_name> ::= <identifier>
```



</dd>
</dl>



<a name="loio1f935a3dff744f7bbf488271a6c869f4__section_kt1_zlm_wcb"/>

## Permissions

To use this statement, you must have the CERTIFICATE ADMIN system privilege.



<a name="loio1f935a3dff744f7bbf488271a6c869f4__section_ugy_xn5_4pb"/>

## Examples

Drop the public key.

```
DROP PUBLIC KEY jwt_pubkey;
```

