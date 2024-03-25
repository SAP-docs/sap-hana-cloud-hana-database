<!-- loiod3eb4231f8f04a0bb917d1a5d6aaae89 -->

# Set up the Python Run Time for Cloud Foundry

Find information about how to set up the Python run time for your Python applications.



<a name="loiod3eb4231f8f04a0bb917d1a5d6aaae89__prereq_ntb_lyz_ddb"/>

## Prerequisites

-   The installed Python run time must be version 3.0 or higher.

-   The Python run time must include `setuptools` and `pip`.

-   At least Python 3 must be installed on the target system \(at the operating-system level; not just the run time\).




<a name="loiod3eb4231f8f04a0bb917d1a5d6aaae89__steps_q4j_lyz_ddb"/>

## Procedure

1.  Set up the application.

    1.  Specify the Python version in the application using the `runtime.txt` or `Pipfile.lock` file included in the root folder of the deployed application.

    2.  Format the Python version as shown in the following example:

        `major.(minor|x)|(.patch|x)`

    3.  Declare the application dependencies either in `requirements.txt`, in `setup.py`, or in `Pipfile.lock`. Both `pip` and `pipenv` are supported for dependencies installation.

    4.  Download application dependencies by putting them in the `vendor` directory at the root of the application.

        The build pack will execute `pip install` using the provided `requirements.txt` file \(or generate a `requirements.txt` file from the provided `Pipfile.lock` file\). If the vendor directory exists, it will be passed to the `pip install` command as an additional parameter.

    5.  Provide a start command for the application, for example, with one of the following options:

        -   A `Procfile` for cases where no start command is provided for the build pack. For more information see *Related Information* below.

        -   The `start` command in the `manifest.yml` file

        -   Provide a Python start script named `server.py` in the root folder of your application. If none of the above options is available, the build pack will start the application with the command `python server.py`.

        -   The `start` command provided in `xs push` with the *\-c* option.



2.  Deploy the Python application.

    > ### Note:  
    > The Python build pack reports an error if there is no run time matching the requested version.


**Related Information**  


[Procfile](https://docs.cloudfoundry.org/buildpacks/prod-server.html)

[Python Programming \(SAP HANA Client Interface Reference\)](https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.latest/en-US/f3b8fabf34324302b123297cdbe710f0.html)

