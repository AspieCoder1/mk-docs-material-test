# ADDING EVIDENCE TO INFORM DATA PREPARATION

In data preparation, a variety of data transformation and cleaning operations are available, and the application of each such operation to each source or subset of sources needs to be informed by evidence.

![Visualising attribute values](https://i.imgur.com/8uJOiCp.png)

In Data Preparer, data context is a type of evidence that provides additional information about the target. This one type of evidence is used to inform decisions in several data preparation steps.

You can modify the data context at the bottom of the page, by navigating to **data context** from the top bar menu.

![Data context menu](https://i.imgur.com/8NKGdeu.png)

Resources can be labeled as the  following three types:

* **Reference data**: The complete list of all the data in a domain. For example, this could be a complete list of town names or zip codes. The correct result of a wrangling process is unlikely to contain all these values, but all correct results should correspond to the data in the reference data.

* **Master data**: The complete list of the relevant data of an application. As an  example, this could be all the suppliers with which an organisation works – where there is a complete such list, it is master data.

* **Example data**: A collection of representative values. These values need not to be expected results of the wrangling process (e.g. they could be made up, or they could be from an earlier wrangling activity).

In the data context tab, the submenu options to *upload reference*, *upload master* and *upload examples* allow the user to identify csv files in which data context data is found. Attribute names in those files that correspond to those in the target are assumed to be related, though such relationships can be added (using add relationship in the submenu) or removed (using the trash icon beside the relevant attribute).

![Upload reference example](https://i.imgur.com/EahX6Wx.png)

## Usages
The additional evidence provided in data context facilitates:

* Refining existing tasks 
> For example, let's assume author names are stored in the column with name *text*. Without data context, the relationship between *text* in the source and *author* in the target, is missed by Data Preparer. However, by providing representative values for the author attribute of the target in the data context, Data Preparer is able to identify the association between the two columns.

* additional data preparation tasks
> For example, repairing the data set: missing values for rating in Riverside Books, can be filled in from the data context. Reformat the data set: the format used for the isbn attribute in Riverside Books, is inconsistent with that in the data context; the isbn data in Riverside Books is reformatted to use the representation in the data context (i.e., without the ISBN prefix).
