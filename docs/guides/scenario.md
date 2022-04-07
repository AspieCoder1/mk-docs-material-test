# Scenarios

## What is a scenario
A scenario is datapreparer's way of representing a project. In datapreparer, you start a wrangle project by first creating a scenario through the scenario wizard. Datapreparer allows you to save your progress and export your project into .scenario files to be shared with other collaborators or to continue your work at another time.

## Create a scenario through the Scenario Wizard
First, click on the big plus button on the bottom right of the screen.

![Start Scenario Wizard](https://i.imgur.com/eI0afTk.png)

Click on the **start wizard** button to launch the scenario wizard.

The wizard will guide you through every step of the process, you can find detailed information on the bottom right at each step.

### Steps
1. Create your target schema.
    - Set how you want your end product data to look like by setting your desired table fields.

2. Add your data sources
    - Add your data sources, csv files, json files, connect your databases etc. Full details in [Adding Data](../adding-data/intro/) section.

3. Set the data context
    - Add additional information about your target to improve the wrangle process by adding reference data, master data and example data. Full details in [Data Context](../viewing-data/) section.

4. Set the user context
    - Set your requirements on the wrangling process by setting criteria or filters. Full details in [User Context](../setting-priorities/intro/) section.

5. Wrangle!
    - Click on the **>>** button to wrangle the data and produce an end product.

6. Feedback
    - Give your own input on the end product, manually select which rows are relevant/non-relevant. Full details in [Refining Solutions](../refining-solutions/intro) section.

7. Repeat step 5-7 until satisfied

## Scenario controls
The datapreparer contains some features for controlling scenarios, which are located under the home tab.

![Scenario control](https://i.imgur.com/KW7m1MW.png)

### Importing scenario
You can import a .scenario file from a previous project or from a collaborator.

### Exporting scenario
You can export a wrangle project into a .scenario file to work on later or share to another collaborator.

### Clear scenario
You can clear a scenario that you don't want to work on anymore. 
> Note: Once a scenario is cleared, you can't get the data back, so think twice before clearing a scenario.