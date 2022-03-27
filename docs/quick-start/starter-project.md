# Example Starter Project
In this section, we will use the datapreparer web interface to introduce a running example that will illustrate the features of Data Preparer. The sample is small enough to be easily understood and presents several data integration and cleaning challenges that need to be resolved during data preparation.

## Prerequisites
To run the example project, you need to have the datapreparer setup and the ManualBooks0.scenario file. This file should have come with the download, or you can download it manually from here. *todo*

## Introduction
The scenario involves an online bookshop that is considering introducing promotions on specific authors and is interested in comparing the prices of its competitors for these authors. With this in mind, it has scraped data on the publications by the authors from several competitor sites to act as sources for the data preparation process. 

#### Two of these (with some example data) are for 
- Rainforest Books (Table 1) and 
- Riverside Books (Table 2). 

![Tables](https://i.imgur.com/4xY47r5.png)

The tables contain certain features that need to be considered during data wrangling that is common in practice (e.g., varying numbers of columns, inconsistent names for columns having the same data, missing values).

## Launching the web interface
Let's launch the web interface (full details in the previous section) to get started. If you have launched it correctly, you should see this page.
![datapreparer homepage](https://i.imgur.com/yMc7TJd.png)

## Import the scenario
Next, let's import the ManualBooks0.scenario file to get some data. The import scenario button is right next to the wrangle button.
![import scenario](https://i.imgur.com/h5WxTim.png)

Once the scenario is imported, you will see that the scenario info section is now populated with information from the imported scenario.
![scenario info](https://i.imgur.com/CnPfpyc.png)

## Viewing the data
We can take a more detailed look at the data by navigating to the data source tab. This tab displays all the data sources for the scenario.
![view data](https://i.imgur.com/8G4BD6F.png)

You can also view the data rows directly by clicking on any data sources. For example, here are the data rows for the **GoodReads** data source.
![data rows](https://i.imgur.com/Nuo6rX0.png)

## Visualisation of the data
For any data table in our scenario, we can visualise its attribute values by clicking the respective chart icon, thus facilitating the discovery of outliers, anomalies, patterns, trends in the data, etc. Furthermore, we can visualise tables in sources or data context, candidate mappings, and the end product. 

#### How attributes are plotted
- Attributes with numeric values are plotted as continuous lines, along with a statistics summary (maximum, minimum, mean, standard deviation, median, and sum).
- Attributes with many values, a distributed sample of a maximum of 1000 values will be plotted, while the statistics summary will still be calculated on the complete data, ignoring empty values. 
- Attributes with string values will be plotted as bar charts, in which the 9 first bar heights correspond to the 9 most frequent terms, while the last item in the horizontal axis refers to the number of the values that are not plotted. 

Here is the visualisation of the attributes in the **GoodReads** table.
![Visualisation](https://i.imgur.com/gClrb0z.png)

## Setting the target
The target section is where you would set your expected output format for the data; this is how the user makes explicit what is required of the wrangling process. Then, the datapreparer will transform the input data sources to fit this format. 

The target for data preparation is also a table definition, just add the fields you want, and the datapreparer will try to match the data sources to them.
![target schema](https://i.imgur.com/BXkzwa2.png)

## Wrangle the data
With this information (i.e. the sources and the target), it is already possible to wrangle the data with a single click; the wrangle option is always available on the left side of the submenu. This will give rise to a result containing several rows specified in the control panel.
> Note: Configurations are set in the control panel section, but we will cover that in a different guide. 

You can view the output rows here in the end product tab.
![end product](https://i.imgur.com/74RZ6sF.png)
> Note: The end product can still contain blank cells, so further data cleaning must be done. You can let datapreparer handle this by setting further configurations, but the datapreparer has managed to link fields from different tables into just one table.

## Viewing the results at each stage of the workflow
In the control panel tab, you can view the workflow of the wrangling process. The workflow contains multiple transducers which transform data from one form to another at multiple stages. We will be covering how these transducers work in detail in another section.
![control panel](https://i.imgur.com/cIjPSfX.png)

You can view the output from each transducer by clicking on any of them.
![transducer in detail](https://i.imgur.com/KEQbudP.png)

## End of example
Congratulations! You have finished going through the basics with datapreparer.

#### Let's review what we just went through
- What just happened? With very little evidence, Data Preparer has had a go at wrangling a collection of sources into a target – here, only a few sources, but there could have been many more.
- Why is this good? This is good because a significant manual effort is required to carry out even preliminary wrangling over a collection of sources in other data preparation systems.

In Data Preparer, an initial result can be obtained much more quickly. Of course, this initial result can be improved upon, but data preparation has been essentially hands-off.