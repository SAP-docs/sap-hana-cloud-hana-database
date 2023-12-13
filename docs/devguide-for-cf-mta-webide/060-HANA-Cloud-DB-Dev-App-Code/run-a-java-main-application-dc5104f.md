<!-- loiodc5104f8ad2040338d0b873c6766b52c -->

# Run a Java Main Application

You can create a Java application that starts its own run time.



## Prerequisites

You are not using any resource configurations.

The resource configurations needed for the database connection are not applicable for the Java Main application. For more information about database connections, see *Related Information*.



## Context

The SAP Java buildpack provides an Apache Tomcat or an Apache TomEE 7 run time. However, you can create a Java Main application to use other frameworks and Java run times such as *Spring Boot*, *Jetty*, *Undertow*, or *Netty*.

> ### Caution:  
> The Tomcat and TomEE 7 run times provided by the SAP Java buildpack have the following functionality:
> 
> -   Solution manager end-to-end tracing
> 
> -   Java EE web container security
> 
>     Java Main applications can only use Spring Security.
> 
> -   Management of exit codes
> 
>     The exit codes are used to monitor started processes. If a process exits with a *0* exit code, it will not be started automatically.
> 
> 
> When you create an application to use its own run time, you have to take into consideration that the above functionality might not be available.



## Procedure

1.  Make sure your built JAR archive is configured properly.

    Regardless of the tool you use to build your Java application, you have to make sure that the following tasks are performed:

    1.  You have built a JAR archive.

    2.  You have specified a main class in the `META-INF/MANIFEST.MF` file of the JAR archive.

        > ### Sample Code:  
        > Sample `MANIFEST.MF`
        > 
        > ```
        > Manifest-Version: 1.0
        > Archiver-Version: Plexus Archiver
        > Built-By: p123456
        > Created-By: Apache Maven 3.3.3
        > Build-Jdk: 1.8.0_45
        > Main-Class: com.companya.xs.java.main.Controller
        > 
        > ```

    3.  You have packaged all your dependent libraries in the JAR file, also known as creating an uber JAR or a fat JAR.


    If you are using Maven as your build tool, you can use the *maven-shade-plugin* to perform the above tasks.

    > ### Sample Code:  
    > An example configuration for the *maven-shade-plugin*
    > 
    > ```
    > <build>
    >   <finalName>java-main-sample</finalName>
    >   <plugins>
    >     <plugin>
    >       <groupId>org.apache.maven.plugins</groupId>
    >       <artifactId>maven-shade-plugin</artifactId>
    >       <version>2.4.3</version>
    >       <configuration>
    >         <createDependencyReducedPom>false</createDependencyReducedPom>
    >         <filters>
    >           <filter>
    >             <artifact>*:*</artifact>
    >             <excludes>
    >               <exclude>META-INF/*.SF</exclude>
    >               <exclude>META-INF/*.DSA</exclude>
    >               <exclude>META-INF/*.RSA</exclude>
    >             </excludes>
    >           </filter>
    >         </filters>
    >       </configuration>
    >       <executions>
    >         <execution>
    >           <phase>package</phase>
    >           <goals>
    >             <goal>shade</goal>
    >           </goals>
    >           <configuration>
    >             <transformers>
    >               <transformer implementation="org.apache.maven.plugins.shade.resource.ServicesResourceTransformer" />
    >               <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
    >                 <manifestEntries>
    >                   <Main-Class>com.sap.xs.java.main.Controller</Main-Class>
    >                 </manifestEntries>
    >               </transformer>
    >             </transformers>
    >           </configuration>
    >         </execution>
    >       </executions>
    >     </plugin>
    >   </plugins>
    > </build>
    > 
    > ```

2.  Configure `manifest.yml`.

    To be able to push the Java Main application, you need to specify the path to the `.jar` archive in the `manifest.yml` file.

    > ### Sample Code:  
    > Sample manifest.yml
    > 
    > ```
    > ---
    > applications:
    > - name: java-main
    >   memory: 128M
    >   path: ./target/java-main-sample.jar
    >   instances: 1
    >   services:
    >   - java_main_hana
    > ```

3.  Push the application to the Cloud Foundry run time.

    For that purpose, use the `cf push` command.




## Example

To create a Java Main application that uses its own run time, perform the following steps:

1.  Download the *sample\_main* application from the company's server and extract it into a local folder.

2.  Navigate \(in a command shell\) to the *sample\_main* directory of the application and build it.

    If Maven is installed on the computer, you can perform this build operation with the command `mvn clean install`.

3.  After the build completes successfully, check that a `sample_main.jar` file is located in the `target` directory.

4.  Open the `sample_main.jar` file and check that the `META-INF/MANIFEST.MF` file contains the *Main-Class* header with a value that is the name of the main class.

5.  Add the path to the JAR file in the `manifest.yml` file.

    This is necessary in order to make sure that the application can be pushed to the target run-time environment. For this reason, add the following line in the manifest file:

    ```
    path: ./target/sample_main.jar
    ```

6.  Finally, push the Java Main application to the Java run-time environment with the following command:

    ```
    cf push sample_main
    ```


**Related Information**  


[Configure a Database Connection](configure-a-database-connection-d462ffc.md "You can configure your application to use a database connection so that the application can persist its data.")

