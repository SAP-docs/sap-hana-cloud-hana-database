<!-- loiof42595956f5b1014bc6cb241d3d75fc2 -->

# ALTER SYSTEM APPLICATION ENCRYPTION Statement \(System Management\)

Manages encryption keys for applications that use the internal data encryption service.



<a name="loiof42595956f5b1014bc6cb241d3d75fc2__sql_alter_system_application_encryption_1sql_alter_system_application_encryption_syntax"/>

## Syntax

```
ALTER SYSTEM APPLICATION ENCRYPTION <encrypt_option>
```



<a name="loiof42595956f5b1014bc6cb241d3d75fc2__sql_alter_system_application_encryption_1sql_alter_system_application_encryption_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<encrypt\_option\>*

</b></dt>
<dd>

Specifies application encryption options.

```
<encrypt_option> ::=
 CREATE NEW KEY
 | CREATE NEW ROOT KEY WITHOUT ACTIVATE
 | ACTIVATE NEW ROOT KEY
```


<dl>
<dt><b>

CREATE NEW KEY

</b></dt>
<dd>

Creates a new, random encryption key for every application.



</dd><dt><b>

CREATE NEW ROOT KEY WITHOUT ACTIVATE

</b></dt>
<dd>

The CREATE NEW ROOT KEY WITHOUT ACTIVATE clause creates a new ACTIVE root key, re-encrypts all application keys using the new key, and records the new key in the redo log.

The new root key is in the PREACTIVE state. A PREACTIVE key is not recorded in the redo log and cannot be used to re-encrypt the application encryption keys. This clause returns an error if a PREACTIVE key already exists. Creating a PREACTIVE application root key allows you to back up the key before using it to encrypt application keys.



</dd><dt><b>

ACTIVATE NEW ROOT KEY

</b></dt>
<dd>

Activates a PREACTIVE key that was previously created by using the CREATE NEW ROOT KEY WITHOUT ACTIVATE clause. This clause updates the state of the PREACTIVE root key to ACTIVE and the previously ACTIVE root key to DEACTIVATED. An error is returned if a PREACTIVE root key does not exist.

This clause re-encrypts all application keys by using the activated root key.



</dd>
</dl>



</dd>
</dl>



<a name="loiof42595956f5b1014bc6cb241d3d75fc2__sql_alter_system_application_encryption_1sql_alter_system_application_encryption_description"/>

## Description

You can use this statement to manage random encryption keys for application encryption and create and activate root keys.

Applications are consumers of the internal data encryption service, such as internal components, like the secure internal credential store, or the SAP HANA secure store. The new keys are stored encrypted with the current root key of the internal data encryption service. The new keys are used after the transaction is committed. No changes are made to data that has already been written to disk.

Use this statement if your company's security policies dictate that you should periodically change the encryption keys being used to store your data, or if you are instructed to do so by SAP Support.

For more information about encryption in the SAP HANA database, see the *SAP HANA Cloud, SAP HANA Database Security Guide*.



<a name="loiof42595956f5b1014bc6cb241d3d75fc2__section_any_gfd_pbb"/>

## Permissions

You must have the ENCRYPTION ROOT KEY ADMIN system privilege to execute this statement.

You must have the ENCRYPTION ROOT KEY ADMIN or RESOURCE ADMIN system privilege to create application encryption keys.



<a name="loiof42595956f5b1014bc6cb241d3d75fc2__sql_alter_system_application_encryption_1sql_alter_system_application_encryption_examples"/>

## Example

Create new encryption keys for all applications.

```
ALTER SYSTEM APPLICATION ENCRYPTION CREATE NEW KEY;
```

**Related Information**  


[Internal Application Encryption Service](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/7a1a582f27404567828a737fc2c2b190.html "The internal encryption service is used internally by applications requiring data encryption.") :arrow_upper_right:

[ENCRYPTION\_ROOT\_KEYS System View](../../020-System-Views-Reference/021-System-Views/encryption-root-keys-system-view-40c7f48.md "Provides information about root keys.")

[APPLICATION\_ENCRYPTION\_KEYS System View](../../020-System-Views-Reference/021-System-Views/application-encryption-keys-system-view-d2c58ec.md "Provides information about encryption keys used by applications.")

[M\_ENCRYPTION\_OVERVIEW System View](../../020-System-Views-Reference/022-Monitoring-Views/m-encryption-overview-system-view-ee1a50a.md "Reports the encryption status for all data at rest where encryption is supported.")

