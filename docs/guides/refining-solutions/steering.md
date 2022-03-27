# Introduction to steering
Steering referes to the process of altering parameters throughout the pipeline to change the final result.
The processing pipeline applied by Data Preparer can be seen at the top of the control panel
tab, as illustrated below.

![Processing pipeline](https://i.imgur.com/XwFCFGB.png)

The control panel allows individual steps to be toggled on and off (all are on, as indicated by the tick symbol), though note that there are dependencies, so deselecting some steps will lead to others being deselected (which is visualised by removing
their ticks). Selecting the play symbol(▷) runs the data preparation process up to that stage, and can allow rapid scrutiny of the results or part of the complete pipeline.


# Individual parameter control

## Matching

* `match strategy`: 
    * schema – use only attribute names for matching. 
    * instance – use only instance evidence when there are instances in the data context, and when not use schema.
    * schema + instances – combine the evidence from schema and instance matching into a single score.

    > We recommend schema + instances, as it takes into account all available evidence.

* `match threshold`: Value in the range 0 to 1. Discards all matches with a score below the threshold. 
> We recommend experimenting with this threshold, though a value of around 0.4 is often appropriate, avoiding lots of spurious matches while including most correct ones.

* `match instances max`: Maximum number of values used in instance matching. 0 means that all the available data is used. 
> Note that with large collections, a high value here will slow down the matching process.

It is possible to exclude a match from data wrangling by clicking on matches text. You can select the area for a match in the exclude column to toggle the exclusion of the match from further processing. 

![Excluding match](https://i.imgur.com/P6AK2ra.png)

Excluding a match means that the associated source attribute will not be considered as a source for data for populating the matched target attribute. Using the same menu, you can insert a match that the system has missed using ``add match`` from the submenu. Selecting add match causes the new match to be created.

## Repair

Data repair will generate functional dependencies strictly, and then use them for repair unless they are switched off.

## Transform

* `minimum percent`:  Minimum percentage of the source values that should participate in the training data for the rule inference. 
> Note: Format transformation infers rules that reformat from source values into the format of corresponding target values.
* `minimum size`: Related to minimum percent, but specified as a number of values instead of a percentage.
* `fail limit`: Controls how many attempts the synthesis algorithm should have before concluding that a transformation cannot be found for an attribute. The fail limit should be less than the minimum size.
* `source limit`: Number of values from the source that will be considered for use in examples (or 0 for unbounded). 
> This should not be less than the minimum size.

> In general, attributes that contain more different formats will require higher values for all these parameters, but higher values lead to longer runtimes. We recommend that none of minimum percent, minimum size or source limit should be below 10, and that fail limit should be 5 or more.

Accessing the transform details by clicking on the card, provides the option to verify the transformations that have been carried out. It is also possible to define custom transformation examples that will instruct
the process how to transform source attribute value. These user-defined examples will be used in conjunction to the ones obtained from the data context. Rather than revealing the internal representation of a rule, here the
user can accept or reject a rule based on its effect.

The user can also add custom transformation expressions to modify the contents of source attributes directly by selecting `add expression`.  Expressions can either modify an existing
attribute, or add a new one with the results of the expression as its contents. For
instance, the expression: UPPER(”source_table”.”attribute”) will convert the values of
the defined attribute to upper case. Expressions can contain any number of functions and attributes. In practice, running an expression will result in an execution of a SQL query of the form: 
```UPDATE source_table SET attribute=expression``` 

Transformations are not part of the wrangling process.
Transformation expressions, as well as attribute reformats, are both executed:
* at the request of the user
* upon scenario initialisation, if the property transform.apply_transformations has been set to yes.
## Profile
### For candidate key descovery:

* `Detect candidate keys`: Whether to search for candidate key attributes or not. This is enabled by default.
* `Max candidate key size`: the maximum number of attributes that can be used in a candidate key. 
> We recommend this is kept quite low (e.g. 1), as the number of candidate keys in tables with many attributes can grow rapidly.


### For inclusion dependency discovery:

* `Overlap threshold`: Only inclusion dependencies with at least this fraction of overlap will be used in joins. 
> Note that inclusion dependencies are kept when the overlap in either direction exceeds the overlap threshold.
* `Matches only`: Restrict inclusion dependency discovery only to source tables that have at least one attribute matching an end product attribute.
* `Candidate keys only`: Restrict inclusion dependency discovery only to attributes that are candidate keys.
> These latter two parameters can be used to reduce the number of inclusion dependencies retained, to those that are most relevant to the wrangling task at hand.

It is possible to exclude an inclusion dependency or a candidate key from data wrangling by clicking on the inclusion dependencies and candidate keys in the explain window. As with matches above, the exclude column can be used to toggle the availability of the inclusion dependency or candidate key in the wrangling process.

> Note: Inclusion dependencies are used in mapping generation to identify when joins can be carried out, so excluding an inclusion dependency means that the attributes in the dependency will not be joined. Similarly, candidate keys are used in mapping generation to determine which attributes are used to join tables, and which join operator to use. As a result, excluding a candidate key will reduce the likelihood that the attributes involved in the key will participate in join conditions.

## Mapping Generation
* `mapping top k`: Maximum number of mappings that will be produced by mapping generation. 
> We suggest starting with a small number (e.g., 10), as evaluating individual mappings can be expensive, and there may be many candidate mappings that provide rather partial answers. If the generated mappings continue to be useful, the number can be increased incrementally.
* `mapping size max`: Maximum number of tables that can contribute to a mapping. This limits the number of joins that can appear in a mapping.
> Note that although data preparer unions the results of different mappings, mappings themselves do not contain the results of union operations.
We suggest starting with a small number (e.g., 5), and checking that the generated mappings make sense.


It is possible to exclude a mapping from data wrangling by clicking on the mappings in the explain window. As with matches above, the exclude column can be used to toggle the exclusion of the mapping from the wrangling process.
> Note that excluding a mapping also excludes mappings that are subsumed by that mapping (i.e. simpler mappings that can be obtained by removing joins from this mapping). As a result, excluding a mapping is quite a blunt instrument; finer grained control over mapping generation can be obtained by editing profiling data.


## Tuple Selection
* `criteria limit`: the number of rows used when evaluating a criterion on a source. Set to 0 for the whole source to be used.
* `product size`: the number of rows to include in the end product.

# Control the Role of Sources
However, as well as steering the steps in the process, Data Preparer also allows the roles of the sources to be individually configured, allowing fine grained control over how they contribute to the data preparation process

For each attribute in a scenario, it is possible to toggle whether or not that attribute should be considered by each of the steps in the data wrangling process. For each of these steps, excluding an attribute means:

* `match`: do not match this attribute with the target, and thus do not use this attribute as a
source of values for the target.
* `repair`: do not fill in empty values for this attribute using repair rules.
* `transform`: do not reformat the values of this attribute.
* `candidate key`: do not consider this attribute for inclusion in a candidate key.
* `inclusion dependency`: do not compute inclusion dependencies for this attribute.
* `join`: do not use this attribute in join conditions.

The action icon to the left of the attributes opens context menu with shortcuts to attribute-specific actions including:

* add to target schema
* add match
* add transformation examples
* reformat attributem
* add transformation expression

## Context usage


| Wrangling Stage | Data Context Types | Comment |
|-----------------|--------------------|---------|
| Matching | Reference, Master, Example | All evidence can be helpful |
| Repair | Reference, Master Repair | needs dependable functional dependencies |
| Transformation | Reference, Master, Example |  Will need comprehensive / consistent data |
| Profiling | | Does not use data context |
| Mapping Generation | | Does not use data context |
| Mapping Selection | Reference, Master, Example | Depending on the criterion |