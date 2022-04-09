# Data Storage
For data storage, we decided to use H2SQL database, which is an **in memory** database. 

## What does this mean?
- This means that there is no data persistency, so all data will be lost once the application is shut down
- This means there is no way to save analysis of data preparation that are in progress.

## How to save data?
By design, we can save our progress of a wrangle session on the browser through the use of scenario files (see [Intro to Scenarios](../../guides/scenario/)) and we can save the end product directly in the command line through the `product.uri` flag (see [Command Line Tool commands](../../advanced/command-line/commands/)). 

But if you really want to configure the database settings, you can change the configs in the `datapreparer/app/src/main/resources/integration.properties` file.