# JSON data support

Data Preparer supports importing JSON format data as well. 


## Importing the data
1. Go to the sources tab
![Sources tab](https://i.imgur.com/IQvHsTG.png)
2. Click **upload sources**. After this you should get a prompt to choose a file.
3. Press **upload**
4. After this step you should see the new data source. It should look something like this,
![Uploaded datasource](https://i.imgur.com/7rGkZRj.png)
5. You have now successfully imported data from a JSON file. From here you can now explore and wrangle the data.

#### Supported structures:
1. With attribute names:

``
[ {"att1": "v1", "att2": "v2", ...},
{"att1": "v3", "att2": "v4", ...}, ... ]
``

or

``
{"data": [{"att1": "v1", "att2": "v2", ...},
{"att1": "v3", "att2": "v4", ...}, ...]}
``

2. Without attribute names:

``
[["v1","v2", ...],["v3","v4", ...], ...]
``

or

``
{"data":[["v1", "v2", ...], ["v3", "v4", ...], ...]}
``