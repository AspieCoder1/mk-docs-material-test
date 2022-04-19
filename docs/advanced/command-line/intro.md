# Command Line Tool
Datapreparer also has a command line version available. 

## Prerequisite
To use the command line version, you need to have Java 11 installed.

## Download
The command line version of the tool can be downloaded here #todo!

## Directory Structure
In the command line version, there is no function to use .scenario files. Instead, the .scenario file is unbundled and broken down into files similar to below, and these files are passed into the command line individually.

When working with the command-line version of Data Preparer, we recommend that the directory structure used for the examples in the zipped archive is adopted for further projects.

```
- scenario-name
    - data
        - data-source1.csv
        - data-source2.csv
        - data-source3.csv
    - data-context.csv
    - feedback.csv
    - sources.csv
    - wrangle1.properties
    - wrangle2.properties
```