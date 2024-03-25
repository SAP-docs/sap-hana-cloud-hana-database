<!-- loio5fdcf7f11e9c4979a83d00e9ca44b67a -->

# Create a Python Application

This topic will guide you through the steps required to create a simple Python application.



## Procedure

1.  Create a new directory called `pyapp`.

2.  Specify the run time version your application needs, by creating a `runtime.txt` file in the `pyapp` directory, with the Python version you have deployed in the target run-time environment.

    > ### Sample Code:  
    > `runtime.txt`
    > 
    > ```
    > python-3.9.18
    > ```

3.  Specify Flask as a dependency for the Python application.

    Since the Python application is a Web server utilizing the Flask Web framework, you must specify Flask as a dependency, for example, by creating a `requirements.txt` file in the `pyapp` directory, with the following content:

    > ### Source Code:  
    > Flask Dependency in `requirements.txt`
    > 
    > ```
    > Flask==3.0.0
    > ```

4.  Create a `manifest.yml` file in the `pyapp` directory, which describes the Python application and how to deploy and run it in the target run-time environment.

    > ### Source Code:  
    > `manifest.yml`
    > 
    > ```
    > ---
    > applications:
    > - name: pyapp
    >   host: pyapp
    >   path: .
    >   command: python server.py				
    > 
    > ```

    > ### Caution:  
    > Cutting and pasting from this code block will probably cause white-space formatting issues in the `yaml` file. After pasting, remember to adjust the indenting to conform to valid yaml.

5.  Create a `server.py` file in the `pyapp` directory, which will contain the application logic.

    In this example, the server returns a ***Hello World*** message, when requested.

    > ### Source Code:  
    > `server.py`
    > 
    > ```
    > import os
    > from flask import Flask
    > app = Flask(__name__)
    > 
    > port = int(os.environ.get('PORT', 3000))
    > @app.route('/')
    > def hello():
    >     return "Hello World"
    > 
    > if __name__ == '__main__':
    >     app.run(port=port)
    > 
    > ```

6.  Push the Python application to Cloud Foundry.

    `cf push`

7.  Check the URL of the deployed Python application.

    After application deployment is complete, use the command `cf apps` to display a list of all deployed applications and the corresponding URL at which each application is reachable. Locate the application `pyapp` and note the assigned URL.

8.  Open a new Web browser and paste the URL of `pyapp` into it.

    `pyapp` displays the following message:

    ***Hello World*** 


