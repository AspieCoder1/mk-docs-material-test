# Data Context

This file describes resources in the data context that should be included in the data wrangling
scenario.

## Format of the file

We have provided an example of how the contents of the file should be structured in **datacontext.csv** in the Manual Books example.

The first 8 columns in this file are identical to the ones describing the [sources](../sources/): uri, tables, description, data, extensions, separator, recursive, overwrite.

However, columns 9, 10, and 11 should be as follows:

| Columns | Explaination |
| ------- | ------------ |
| **type** | The data context type of the resource. It can be any of the following: example for example values, master for master data, and reference for reference data. |
| **included (optional)** | A comma-separated list of the fields of the imported resource to include in the created data context relationship. List items are in the form field1:field2, where field1 is one of the product field names, and field2 is a field in the resource that is imported. If none is specified here, the data context relationships will be created between fields that share the exact same name in the end product and the newly imported resource. E.g. the entry *name:newfield1*, *description:newfield2* means that relationships between the target schema attributes name and description, and the resource attributes newfield1 and newfield1, should be created, respectively. |
| **excluded (optional)** | A comma-separated list of fields of the imported resource to exclude from the data context relationship, as the column included described above. Note, a resource-level and an entity-level relationship will still be created for the imported resource. |
