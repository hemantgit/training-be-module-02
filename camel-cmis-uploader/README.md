# Backbase Training Exercises

## Portal Backend - Module 2: Camel CMIS Uploader

This exercise is part of [Module 2: Content Services](../../..)

In this tutorial, you will develop a Camel based component which listens to the specified directory on file system and automatically uploads file copied to this directory to the Content Services repository.

### Installation & Configuration

- Copy **camel-cmis-uplpoader** into the **services** folder of your Launchpad 0.12.x project.

- Include **camel-cmis-uploader** module to the build. Open `services/pom.xml` and add **camel-cmis-uploader** in the `<modules>` section:
	```xml
	    <modules>
	        ...	    
	        <module>camel-cmis-uploader</module>
	        ...
	    </modules>
	```	
	Re-compile **services** by executing `mvn clean install` in the **services** folder.
	
- Enable the newly created module in the Portalserver application. In the `<dependencies>` section of `webapps/portalserver/pom.xml`, add the following dependency:

	```xml
	    <dependency>
	        <groupId>com.backbase.training</groupId>
	        <artifactId>camel-cmis-uploader</artifactId>
	        <version>1.0-SNAPSHOT</version>
	    </dependency>
	```

- Configure module properties. Edit `configuration/src/main/resources/backbase.properties` file and add the following property specifying the path to the file system directory which will be monitored for file system operations.

  ```
  training.services.cmis.import.dir=absolute_path_to_monitored_folder
  ```
  And now we need to add the location of the Atom service document, so also we need to edit this property:
  
  ```
  orchestrator.contenthost.atompath=http://${contentservices.host}:${contentservices.port}/${contentservices.context}/atom
  ```

  Re-compile configuration module by running `mvn clean install` command from the **configuration** module.

- Configure logging (optional). Add the following line to your **logback.xml**

  ```xml
  <logger name="com.backbase.training" level="DEBUG"/>
  ```

### Build & Run

- If Portalserver application is already running, stop it by pressing *Ctrl+C*. Start Portalserver application by executing `mvn clean jetty:run` command from the **webapps/portalserver** directory.
- If Content Services application is already running, stop it by pressing *Ctrl+C*. Start Content Services application by executing `mvn jetty:run` command from the **contentservices** directory.
- Place some file in the folder configured for monitoring. 
- Open CXP Manager Assets and make sure that newly uploaded file appears there.
