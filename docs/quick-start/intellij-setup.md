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

## Setting up the maven module
Go to **File > Project structure** or <kbd>&#8984;</kbd> + <kbd>;</kbd> after doing this you should should see the following menu.
![Project structure](https://i.imgur.com/3JjeqR5.png){.center}
At this point you should set the project SDK to Java 11 as well as the language level. 
From here we go on to the modules tab, press the blue + button and choose the **new module** and the maven option.
After completing this step you should get the following menu,
![New module](https://i.imgur.com/1Kr5Nkr.png){.center}
You should click the **next** button.
At this point you will be prompted to add choose a name and location of the module.
The location should be the **app** directory in the datapreparer root and the name can be what ever you choose. The completed configration should look like this,
![Complete module configuration](https://i.imgur.com/CC6ujkZ.png)
After this you should press finish. You have now set up a maven module for the application.
> *IMPORTANT*: you will need to copy and paste the pom.xml into from the repo app folder,
>  it is overwritten locally by the IntelliJ.
> It is avaliable [here]().
## Creating run configurations
The final step is the run configuration.
We go into the top right hand corner next to the run button.
There is a dropdown to the left of it, cliock this dropdown and select **edit configurations...**.
There you should create a new Spring Boot runner.
The configuration for which is given below,
![Run configuration](https://i.imgur.com/qm2V16t.png)
> IMPORTANT: the JVM option must be set to 
> `
> -Djava.awt.headless=false -Dapple.awt.UIElement=true -Dtextdb.allow_full_path=true
> `
> for the application to run properly.
## Running the datapreparer app
This step is very easy. We simply just select the created run configuration from the dropdown and press the green run button.

Congratulations you now have datapreparer setup with IntelliJ IDEA.