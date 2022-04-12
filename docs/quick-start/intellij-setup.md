# IntelliJ setup
> **_NOTE:_** The project now includes a .idea folder which should handle all the set up for you.
> This guide is in case that setup does not work as expected.

This section will go through the steps to set up the datapreparer tool to run in IntelliJ IDEA.

## Prerequisites
Running the code in IntelliJ requires the following prerequisites:

- IntelliJ idea installed on your local machine
- Java 11
- Maven 3
- The codebase cloned into an IntelliJ project and imported as a maven project with a Java 11 SDK configured.

## Setting the maven project
Go to **File > Project structure** or <kbd>&#8984;</kbd> + <kbd>;</kbd>. After doing this the following menu will be displayed:
![Project structure](https://i.imgur.com/3JjeqR5.png){.center}
At this point, you should set the project SDK to Java 11 and the language level. 
Go to the modules tab, press the blue + button and choose the **new module** and the maven option.
After completing this step, you should get the following menu,
![New module](https://i.imgur.com/1Kr5Nkr.png){.center}
Click the **next** button.
Use the prompt to choose the name and location of the module at this point.
Keep the default name. 
The completed configuration should look like this,
![Complete module configuration](https://i.imgur.com/VJj89Oh.png){.center}
A maven project sidebar should be visible.
IntelliJ will now look like this,
![IntelliJ with maven config](https://i.imgur.com/IvhVgix.png){.center}

## Fixing Java version in maven
You now need to set the Java version in the pom.xml file.
You can do this by adding the following lines to pom.xml inside the app directory:

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.8.1</version>
    <configuration>
        <source>11</source>
        <target>11</target>
    </configuration>
</plugin>
```

## Adding the datapreparer maven configuration
We now need to add the maven configuration for the *app* directory, which contains the application source code.
If you look at the maven tab, you will see a small plus button.
Click on the small plus button in the maven tab as shown:
![Maven tab](https://i.imgur.com/iUFpkii.png){.center}
Click on this add button.
The following prompt is to select the location of the pom.xml file for the configuration you would like to add.
Navigate to the app directory and select the pom.xml file inside of it.


## Creating run configurations
The final step is the run configuration.
We go into the top right-hand corner next to the run button.
There is a dropdown to its left; click this dropdown and select **edit configurations...**.
There you should create a new Spring Boot runner.
The configuration which is given below,
![Run configuration](https://i.imgur.com/qm2V16t.png){.center}
> **IMPORTANT: the JVM option must be set to 
> `
> -Djava.awt.headless=false -Dapple.awt.UIElement=true -Dtextdb.allow_full_path=true
> `
> for the application to run correctly.**
## Running the datapreparer app
This step is straightforward. Simply select the created run configuration from the dropdown and press the green run button.

Congratulations, you now have datapreparer setup with IntelliJ IDEA.