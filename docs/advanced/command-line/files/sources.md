# Sources

The file describing how to access the sources, passed as an argument to the -s command line option

## Format of the file
We have provided an example of how the contents of the file should be structured in **sources.csv** in the Manual Books example.

The csv file is expected to contain exactly the following columns:

1. uri. A jdbc connection string to an external database, as described in [Adding Data Uri](../../../../guides/adding-data/local-DB/). If a uri
is not specified here, then the source entry should be defined in column data.

2. tables. Optionally, in case a uri is provided, a comma-separated list of the specific tables in the database schema to consider in the wrangling process. If none is specified, all tables will be considered.

3. description. Optionally, a description of the resource.

4. data. A file directory, or a delimiter-separated text file. The file path can be either absolute, or relative to the location of the Data Preparer executable. The first line in each source file is expected to contain the field names. The delimiter can optionally be defined
in the separator column.

5. extensions. A comma-separated list of file extensions. In case a directory is specified in the data column, we can optionally filter by extension the files to wrangle. E.g. csv, tsv.

6. separator. Optionally, an explicit separator character to use when parsing a delimiterseparated text file defined in the data column. The delimiter can be a comma, a tab, a colon, or a pipe (, or \t or : or |). If none is specified, the separator character will be autodetected.

7. recursive. In case a file directory is specified in the data column, we defined here whether the system should also scan its subdirectories for data files to import. 
> Default is false.

8. overwrite. When a uri is defined, we can choose whether the uri contents are retrieved and overwrite the locally cached ones every time a wrangling process starts. In case both a connection to a Postgres database and a data file are defined in the uri and data columns respectively, we can choose whether the database contents will be overwritten by the data file contents. 
> Default is false.

9. exclusions. A comma-separated list of fields in the source and the respective wrangling steps from which they should be excluded. For instance, an entry table1.field1:repair, table2.field2:ckey, means that attribute field1 in table1 should not be repaired, and attribute field2 in table table2 should not be a candidate key. 
> Wrangling steps that can be excluded are: match, repair, transform, ckey, ind, join.

10. matches. A comma-separated list of user-definedmatches of source fields to target schema fields, in the form: 
> table1.field1:end_product_table:field2.

11. examples. A comma-separated list of user-defined transformation examples of the form **source value -> target value**. The contents of this field should be included in double quotes, so as to ensure that parsing the csv file is not affected.