# Select transducer

## How it works
Tuple selection is the final step of the Datapreparer pipeline.
It takes in the generated candidate mappings and applies all the joins to the data.
Datapreparer combines the mappings to produce the output of the wrangle, what we call the **end product**.
The output file can be downloaded as a CSV, Excel, JSON or avron file.
You can then upload this file to a database or storage medium.

## An example
We will again consider the *ManualBooks1* scenario.
If you go to last wrangle results and click *tuple selection*, you will see the following page:
![Tuple selection](https://i.imgur.com/7On5cux.png)
We get the following columns as a result:

- **mapping** - gives the id and link to the mapping applied
- **provenance** - what mapping occurs and the data sources involved
- **completeness** - the percentage of values that are blank in the resulting tuples
- **size** - number of tuples in the mapping
- **selected tuples** - number of tuples selected from the mapping

## Accessing the output
The final step is to view the output of the wrangle.
This is accessible from the **end product** tab.
An example output is something like this,
![Datapreparer output](https://i.imgur.com/tyo1Z4p.png)
You can then click the download icon next to the table name and select the file type you want to download.
You now have access to the wrangle output!