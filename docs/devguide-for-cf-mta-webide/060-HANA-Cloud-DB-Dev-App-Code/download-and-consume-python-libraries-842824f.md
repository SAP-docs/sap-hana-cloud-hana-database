<!-- loio842824f04d654ceeaf5168da663a65ce -->

# Download and Consume Python Libraries

Python client libraries developed by SAP on the Python Package Index \(PyPI\).



## Context

A selection of SAP-specific and ready-to-use Python client libraries is available for download from the Python Package Index \(PyPI\). To download the SAP Python Client libraries, perform the following steps:



## Procedure

1.  Download the client libraries from the Python Package Index \(PyPI\).

    The most recent versions of the SAP Python client libraries are available for download on the Python Package Index \(PyPI\). Newer client packages might require a more recent version of Python. For more information, see *Related Information* below.

2.  Extract the contents of the Python packages into a folder in your local file system, for example `sap_dependencies`.

    The overall recommendation for applications is for them to be deployed as self-contained. For this reason, applications need to include all of their dependent packages so that the staging process does not need to make any network calls. The Python build pack provides a mechanism for this; applications can make provision for their dependencies by creating a `vendor/` directory in the application's root directory and executing the following command to download \(*\-d*\) the dependent packages and save them in the `vendor/` directory:

    ```
    pip download -d vendor -r requirements.txt –-find-links sap_dependencies
    ```

    > ### Note:  
    > The `pip download` command performs the same dependency-resolution and downloading steps as `pip install`. Instead of installing the dependencies, however, `pip download` collects the downloaded distributions in the specified directory \(the default is the current directory\). To facilitate offline or locked-down package installation, this directory can later be passed as a value to `pip install --find-links`. For more information, see **pip download** in *Related Information* below.

    Make sure you are always downloading packages for the correct platform. Your application must package the dependencies for the platform it will run on. For example, if you are packaging your application in a Windows OS environment, but the run time where the application will be deployed is running on SLES, you must package the Python dependencies for SLES, for example, by including the *\--platform* option in the `pip download` call.

    You should also always ensure the correct dependencies for the corresponding Python run-time version, that is; the run-time version that your Python application will run on. Either execute the `pip download` command with the same Python version, or pass the *\--python-version* flag.

    For more information, see **pip download** in the *Related Information* below.


**Related Information**  


[pip download](https://pip.pypa.io/en/stable/reference/pip_download/)

[The Python Package Index \(PyPI\)](https://pypi.org/search/?q=sap_instance_manager)

[Standard Python Packages for Cloud Foundry](standard-python-packages-for-cloud-foundry-8732609.md "A list of Python packages developed by SAP, which are available for download and use from the Python Package Index (PyPI).")

