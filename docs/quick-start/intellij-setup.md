# IntelliJ setup
> **_NOTE:_** The project now includes a .idea folder which should handle all set up for you.
> This guide is incase that setup does not work as expected.

In this section, we will be going through the steps to setup the datapreparer tool to run in IntelliJ IDEA.

## Prerquesites
Running the code in IntelliJ requires the following prequisites:

- IntelliJ idea installed on your local machine
- Java 11
- Maven 3
- The codebase cloned into a IntelliJ project and imported as a maven project with a Java 11 SDK configured.

## Setting the maven project
Go to **File > Project structure** or <kbd>&#8984;</kbd> + <kbd>;</kbd> after doing this you should should see the following menu.
![Project structure](https://i.imgur.com/3JjeqR5.png){.center}
At this point you should set the project SDK to Java 11 as well as the language level. 
From here we go on to the modules tab, press the blue + button and choose the **new module** and the maven option.
After completing this step you should get the following menu,
![New module](https://i.imgur.com/1Kr5Nkr.png){.center}
You should click the **next** button.
At this point you will be prompted to add choose a name and location of the module.
Keep the name it gives you. 
The completed configration should look like this,
![Complete module configuration](https://i.imgur.com/VJj89Oh.png){.center}
From here you shoud get a maven project sidebar.
Your IntelliJ should look something like this,
![IntelliJ with maven config](https://i.imgur.com/IvhVgix.png){.center}

## Fixing Java version in maven
You now need to set the java version in the pom.xml file.
You can do this by adding the following lines

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
This screen shot shows the tab and the plus button,
![Maven tab](https://i.imgur.com/iUFpkii.png){.center}
Click on this add button.
You will then be prompted to select the location of the pom.xml file for the configuration you would like to add.
Navigate to the app directory and select the pom.xml file inside of it.


## Creating run configurations
The final step is the run configuration.
We go into the top right hand corner next to the run button.
There is a dropdown to the left of it, cliock this dropdown and select **edit configurations...**.
There you should create a new Spring Boot runner.
The configuration for which is given below,
![Run configuration](https://i.imgur.com/qm2V16t.png)
> **IMPORTANT: the JVM option must be set to 
> `
> -Djava.awt.headless=false -Dapple.awt.UIElement=true -Dtextdb.allow_full_path=true
> `
> for the application to run properly.**
## Running the datapreparer app
This step is very easy. We simply just select the created run configuration from the dropdown and press the green run button.

Congratulations you now have datapreparer setup with IntelliJ IDEA.