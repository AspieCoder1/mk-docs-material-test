# Wrangle Properties
In the command line version, the wrangle properties in the control panel tab in the web browser detailed in the [Steering Section](../../../../guides/refining-solutions/steering/) can also be specified in a properties file, eg. **wrangle.properties** and passed to Data Preparer using the -p command line option. 
> Note: We use .properties as our naming convention, but you are free to use whatever name you like.

## Format of the file
We have provided an example of how the contents of the file should be structured in **wrangle1.properties** and **wrangle2.properties** in the Manual Books example.
The properties in this file are expected to be as described below:

### General Settings
- workflow. The system components that will participate in the wrangling process. This
is a comma-separated list, containing any of the following: match, repair, transform, profile, map, select. Note that some of these components require the output of others, as follows:
    - repair requires match; 
    - transform requires match;
    - map requires match, profile; 
    - and select requires map, match, profile.

    > Note: A required component will be executed, even if it is omitted here. For instance, defining a workflow as map, select, will trigger execution of
the workflow match, profile, map, select, because match and profile are required by map. 
The default workflow includes all components: match, repair, transform, profile, map, select.


- workflow.incremental. Setting the value of this property to no, means that when a new wrangling process is executed, all components will be executed. Setting it to yes, means that when a new wrangling process is executed, any existing results will be reused i.e. components whose configuration hasn’t changed since the last run will not run again. 
> The default value is yes.

- product.name. The end product table name.

- product.fields. A comma-separated list of the end product fields and their exclusions. Exclusions from wrangling steps can be defined here as colon-separated sets following the names. 
> Wrangling steps that can be excluded are: repair, transform, join. 

    > For instance, defining product fields as name:repair:transform, desc:transform:join means that the end
product will comprise two fields, name anddesc, while source attributes matching to name
will not be repaired and will not be transformed, and source attributes matching to desc
will not be joined to any other attributes. Note that these are slightly different from the
workflow steps defined in the workflow property above.

- product.uri. This describes the connection to an external database, where the end product should be stored, so that it remains available even after Data Preparer exits. The jdbc uri must also contain the login credentials, as described in [Adding Data Uri](../../../../guides/adding-data/local-DB/). 
> The default value is an empty string, which means the end product will be stored in memory for as long as the application runs. Note that any pre-existing data in this uri will be overwritten.

- filters and criteria. These two properties describe the [User Context](../../../../guides/setting-priorities/intro/), i.e. your preferences over the characteristics of the end product. The filters are hard constraints on the end product, meaning that the end product should satisfy these constraints. 

    Criteria and filters can be of any of the following types:

    Standalone, that require no parameters for their evaluation.

        - completeness. The fraction of the values that are null or empty.
        - tuple_completeness. The fraction of the tuples with non-null, non-empty values. Can only be evaluated on a table.
        - numeric. The fraction of the values that are numbers.
        - datetime. The fraction of the values that represent a date or a time.
        - is_email. The fraction of the values that are emails.
        - is_uri. The fraction of the values that are uris.
        - contain_numbers. The fraction of values that contain any number.
        - contain_letters. The fraction of values that contain any letter.
        - contain_punctuation. The fraction of values that contain punctuation characters, i.e. characters that are not letters, or numbers, or whitespace.
        - contain_email. The fraction of the values that contain emails.
        - contain_uri. The fraction of the values that contain uris.

    Data context-related, that require the presence of data context.

        - data_context_completeness. The fraction of the values that are included in the Master Data or the Example values.
        - data_context_consistency. The fraction of the values that are included in the Reference Data or the Example values.

    Feedback-related, that require the presence of user feedback.

        - relevance. The fraction of the values that the user has marked as relevant.

    > An example of a filter is completeness:product.name:no, which means that the attribute name of the end product table product must be complete. The no in the end is optional, and means that the filter is not inverted. Criteria are defined in the same way, with the addition of weights. An example definition of criteria is: completeness:product:0.5:yes, relevance:product.name:0.5:no.

### Match Transducer
- match.strategy. This can be any of: schema, instances, schema+instances. When the match strategy is set to schema, only attribute names will be compared for similarity. When set to instances, only attribute instances will be compared for similarity. When set to schema+instances, both attribute names and instances will be compared for similarity.
> The default value is schema.

- match.threshold. Matches scoring below this similarity threshold will be discarded. 
> The default value is 0.4.

- match.instances.max. The number of instances to compare when evaluating similarity between two attributes. 
> The default value is 1000.

- match.exclude. A colon-separated set of matches to be excluded from the wrangling process. Matches are declared between any source attribute and any target schema attributes. Source attributes are of the form schema.table.attribute, while target schema attributes are of the form table.attribute. 
> An example of a match is: schemaA.tableA.attrA~end_product.attrX. By default, no matches are excluded.

### Repair Transducer
- repair.apply_rules. When set to yes, the discovered repair rules will modify the sources. When set to no, you can verify the changes and choose whether to discard or apply them. In case of sources in external databases, their contents will not be modified. Only their copies that are imported in Data Preparer will be modified. 
> The default value is no.

- repair.rule.exclude. A comma-separated set of repair rules to exclude. The rules are defined in the form schemaA.tableA.attrA -> schemaB.tableB.attrB, where the values of attribute attrA determine the values of attribute attrB. As such, attrA is the determinant attribute, and attrB the dependent attribute. 
> By default, no repair rules are excluded.

### Transform Transducer
- transform.examples_minpercent. The minimum percentage of the source used to create an example pair. The default value is 10, which means that a minimum of 10 percent of the source values will be used to create an example pair.

- transform.examples_minsize. The minimum number of source values used to create an example pair. The default value is 10, which means that a minimum of 10 distinct source values will be used to create an example pair.

- transform.fail_limit. The number of example candidates that are allowed to fail before the entire set is rejected. 
> The default value is 2, which means that if 2 or more of the discovered example candidates fail, the whole example set for these attributes will be rejected.

- transform.source_limit. The amount of data considered from the source.
> The default value is 0, which means that all data from each source will be considered.

- transform.apply_transformations. When set to yes, the learned transformation examples will result in transformations that will modify the sources. When set to no, you can verify the changes and choose whether to discard or apply them. In case of sources in external databases, their contents will not be modified. Only their copies that are imported in Data Preparer will be modified. 
> The default value is no.

- transform.example.exclude. A comma-separated set of transformation examples to be excluded from the wrangling process. 
> The examples are of form: **source value -> target value**. When values contain commas, the whole examples should be included in double quotes.


### Profile Transducer
- profile.detect_ckeys. Detect candidate keys in the available sources. 
> The default value is yes.

- profile.ckey.size.max. The maximum number of attributes comprising a candidate key. 
> The default value is 1.

- profile.ckey.exclude. A comma-separated set of candidate keys to exclude from the wrangling process. Candidate keys can containmore than one attribute, and they are expressed as colon-separated lists of these attributes. 
> An example of a candidate key consisting of two attributes is schemaA.tableA.attrA:schemaB.tableB.attrB.

- profile.detect_inds. Detect inclusion dependencies in the available sources. 
> The default value is yes.

- profile.ind.overlap.threshold. Inclusion dependencies with an overlap below this threshold will be discarded. This means that only attributes with an overlap above this threshold will be considered for a full outer join. 
> The default value is 0.5.

- profile.ind.matches_only. Only calculate inclusion dependencies in which at least one attribute matches the target schema. 
> The default value is no.

- profile.ind.ckeys_only. Only calculate inclusion dependencies in which at least one attribute is a candidate key. 
> The default value is yes.

- profile.ind.exclude. A comma-separated set of inclusion dependencies to exclude from the wrangling process. 
> An example of an inclusion dependency is: schemaA.tableA.attrA < schemaB.tableB.attrB, which means that the inclusion dependency between attributes attrA and attrB will be ignored.

### Mapping Transducer
- mapping.output.top_k. The maximum number of candidatemappings that will be produced by the mapping generator. 
> The default value is 100.

- mapping.size.max. The maximum number of relations in each candidate mapping. 
> The default value is 10.

- mapping.exclude.generation. A comma-separated set of candidate mappings to exclude from generation. This means that the candidate mappings listed here will not be generated. 
> An example of a candidate mapping to be excluded is: schemaA.tableA [Join attrA = attrB] schemaB.tableB, which joins tables tableA and tableB, which are in sources sourceA and sourceB, respectively, on attributes attrA and attrB.

- criteria.limit. Limit the number of tuples when evaluating criteria. 
> The default value is 0, for unlimited.

- product.size. The number of tuples to include in the end product. 
> The default value is 100.

- product.full_mappings. When set to no, end product will contain exactly as many tuples as defined here. When set to yes, the mapping selection component will keep selecting full mappings until it goes above the number of tuples defined here. 
> The default value is no.

### Select Transducer
- selection.exclude.mapping. A comma-separated set of candidatemappings to exclude from selection. This means that regardless of whether these mappings have been generated by the mapping generation component, no tuples will be selected from them to populate the end product. 
> An example of a candidate mapping is: schemaA.tableA[Join attrA = attrB] schemaB.tableB, which joins tables tableA and tableB, which are in sources sourceA and sourceB, respectively, on attributes attrA and attrB.