# Wrangle Pipeline
In this section, we will be going over the code for the wrangle pipeline.

The main code for handling the pipeline is in `app/src/main/java/com/tdvf/client/ClientImpl.java`.

## How to build a custom component
If you ever feel that the datapreparer's pipeline is lacking to reach your desired results, you can modify the wrangle pipeline to include a custom transducer. In this section, we will be going over how you can add a custom transducer to the wrangle pipeline.

### Steps
1. Create a folder with your transducer name under `app/src/main/java/com/tdvf/transducer`.

2. Create a main class for your transducer and have it implement the `TransducerInterface` class. The convention is to include the word Transducer at the end of the filename.

3. Implement the execute and getType methods.

4. Add it to the workflow under `app/src/main/java/com/tdvf/client/ClientImpl.java`. 