<!-- loio9d8172614c6f486aa62dd108281a6c8f -->

# Naming Conventions in SAP HDI

Rules and restrictions apply to the names of artifacts in the SAP HDI virtual file system

In SAP HANA Deployment Infrastructure \(HDI\), bear in mind the rules listed below when specifying the name of a database object that is deployed to a HDI container and written to the HDI virtual file system. For HDI run-time objects and their name spaces, valid characters are those that are also valid for catalog names \(described in the SAP HANA SQL Reference Guide\), except for the following restrictions:

-   Name space names cannot contain the forward-slash character \(/\).

-   The backslash \(\\\) can be used but must be escaped in the `.hdbnamespace` file with a second backslash.

-   Name space and object names cannot contain the colon character \(:\)

-   The double-colon \(::\) is used as separator between the name space and the object name.

-   The name space name can be empty, in which case no separator is used. If a name space **is** used, then object names must include the declared name space as a prefix, for example, <code><i class="varname">&lt;namespace&gt;</i>::myObject</code>


> ### Restriction:  
> Due to catalog rules, the maximum length of the fully qualified object name \(including the name space\) is 127 characters.

In the HDI virtual file system, the following restrictions apply to the names of files and folders:

-   Names can include only a subset of ASCII, namely, the following characters:
    -   Lower- or upper-case letters \(aA-zZ\)
    -   Digits \(0-9\)
    -   In addition to the standard characters listed above, HDI files and folders can also include the following special characters:

        ! \# % & ' \( \) + , - . ; = @ \[ \] ^ \_ \` \{ \} ~


-   The maximum length of the object's name \(including the path to the source file\) is 255 characters in the HDI virtual file system.
-   The forward slash \(/\) is used as the folder delimiter in the HDI path:

    `path/to/HDI/object.hdbsuffix`

-   An HDI path must **not** start with a forward slash \(/\). Only relative paths are permitted, for example:

    `path/to/HDI/object.hdbsuffix`

-   Trailing spaces ‘ ‘ or periods ‘.’ are not allowed in the name of an HDI file or folder
    -   Trailing space:

        <code>path/to/HDI/object.hdbsuffix<i class="varname">&lt;trailing space&gt;</i></code>

    -   Trailing period:

        `path/to/HDI/object.hdbsuffix.`


-   For HDI folders:
    -   An empty path denotes the root folder

    -   Other paths must end with a forward slash \(/\)

        -   `path/`

        -   `path/to/`

        -   `path/to/HDI/object/`




