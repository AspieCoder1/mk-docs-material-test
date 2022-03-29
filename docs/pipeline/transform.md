# Transform Component

## What it does
A format transformation is a change to the way that attribute values are presented. 
#### For example, 
- names in different sources could be of the form Forename Surname or Firstname Surname
- URLs can be written with or without the protocol (http, https). 

## How it works
In Data Preparer, the data context is assumed to provide the preferred representation for a type of data, and attributes that are used to populate a target attribute for which there are values in the data context may have their formats transformed to reflect that in the data context. 

> Note: As the format transformation is inferred from examples, in practice format transformation only takes place when there are plenty examples in the data set and in the data context, and when the attributes in question have some form of regular structure (as in the date and URL examples above).

## Example
In the explain page in the figure below, format transformations are described in terms of examples used for training, rather than the more difficult to interpret inferred rules. We can see that in the book promotions example, values in Riverside.isbn that have an ISBN prefix have been reformatted to have this removed, reflecting the representation in MasterData.isbn, and indeed that this transformation has been applied 20 times.

![transformation](https://i.imgur.com/x01T3L5.png)

## Configurations in the control panel
Format transformation infers rules that reformat from source values into the format of corresponding target values. 
![transformation-config](https://i.imgur.com/ihf4w2U.png)

#### Format transformation parameters:
- **minimum percent**: This parameter indicates the minimum percentage of the source values that should participate in the training data for the rule inference.
- **minimum size**: This parameter is related to minimum percent, but is specified as a number of values instead of a percentage.
- **fail limit**: This parameter controls how many attempts the synthesis algorithm should have before concluding that a transformation cannot be found for an
attribute. The fail limit should be less than the minimum size.
- **source limit**: This parameter is the number of values from the source that will be considered for use in examples (or 0 for unbounded). This should be more than the minimum size.

> Note: In general, attributes that contain more different formats will require higher values for all these parameters, but higher values lead to longer runtimes. We recommend that none of minimum percent, minimum size or source limit should be below 10, and that fail limit should be 5 or more.

## Steering transformations
### Add examples
It is also possible to define custom transformation examples that will instruct the process how to transform source attribute values. This is done by selecting add examples from the submenu. 

![add-examples](https://i.imgur.com/fsmCaDo.png)

![add-examples-submenu](https://i.imgur.com/i4DzHD2.png)

These user-defined examples will be used in conjunction to the ones obtained from the data context. Rather than revealing the internal representation of a rule, here the user can accept or reject a rule based on its effect. Selecting the eye icon in the verify column 

![eye-icon](https://i.imgur.com/YASZjaU.png) 

gives rise to the display in the figure below, where the specific changes that have been made to the values in the isbn column can be seen. The user can then approve or reject the transformation using the buttons above the table

![detailed-changes](https://i.imgur.com/l51zfjC.png)

### Reformat
From the submenu it is also possible to reformat source attributes to make them more consistent with those in the target. 

![reformat-button](https://i.imgur.com/2MhNprC.png)

![reformat](https://i.imgur.com/RkQZvYF.png)

This is done by explicitly associating multiple (1 or more) source attributes with multiple target attributes. As a result, a derived table can be populated, with the reformatted source contents, informed by training data from the data context. 

As an example, consider a source table that contains an address attribute, while the target schema contains attributes number, street, and town. In order to make this source more consistent with the target, address can be aligned to number, street, town.

> Note: The many-to-many reformatting in this case is informed using data from the data context, though in this case the training data should all come from the same table in the data context. The data context must contain data that can be aligned with every distinct pattern of values in the source. 

![reformat-example](https://i.imgur.com/M7HltV9.png)

So for example, if here are address values of the form 15 Cardiff Road, Swansea and 26 Mauldeth Road South, Manchester, then there will need to be examples that cover street names containing two and three words in the data context, and at least one of these examples should contain similar literal values to those in the source. This is most likely to be achieved without creating custom training data when the data context contains reference or master data. When attribute reformatting is successful, a new table is created, in the same source as the original source table.

### Add expression
From the submenu, the user can also add custom transformation expressions to modify the contents of source attributes directly by selecting add expression.

![add-expression-button](https://i.imgur.com/l3sDTKl.png)

![add-expression-example](https://i.imgur.com/aLEmGYR.png)

Expressions can either modify an existing attribute, or add a new one with the results of the expression as its contents. For instance, the expression: UPPER(”source_table”.”attribute”) will convert the values of the defined attribute to upper case. 

Expressions can contain any number of functions and attributes. In practice, running an expression will result in an execution of a SQL query of the form: UPDATE source_table SET attribute=expression. Transformations are not part of the wrangling process.

## When it runs
Transformation expressions, as well as attribute reformats, 
#### are both executed: 
1. at the request of the user, and 
2. upon scenario initialisation, if the property transform.apply_transformations has been set to yes.