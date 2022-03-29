# Map transducer

## How it works
This transducer takes in all the data sources, relationships and similarity scores genertated by profiling.
The data is then joined together to create combined data sources.
To access this you click on the **mapping generation node** in the *latest wrangle result section*.

## An example
If we run the provided *ManualBook1.scenario* file and perform the wrangle you will get the following output:
![Mapping selection output](https://i.imgur.com/F2JfCYn.png)
So what does this mean?

This output tells us that datapreparer has found three *candidate mappings* between data sources.
These are:

- Riverside and RiversideBooks on the title column
- Riverside and TitleAuthor on the title column
- GoodRead and TitleAuthor on the title column

If we look carefully we can see that datapreparer says an outer join can be performed on these columns.
This is done automatically for us.

## Viewing a mapping
If you look at the output in the above example you will see that the mapping name is highlighted.
Clicking on this gives us some key details of the mapping.
Here is the result of clicking *m02*:
![m02-page](https://i.imgur.com/mjrGGDN.png)
On this page we can see:

- **provenance** - the data sources used in the mapping
- a diagram that shows the mapping as a input/output diagram.
    Clicking on each element inside the diagram gives you the ability to view user context, data sources, attributes and properties.
- a table view of the joined data
  
> If you want to explore the original data you can click a on a datasource and you will be taken to that page.