# Prioritizing Results using Criteria

## How it works
- The **User Context** contains a collection of criteria, each identifying a feature of the result that is important to the user. 
 - Each criterion has a weight set by the user. This is used to indicate the importance of criteria compared to each other. 
- These criteria are used by Data Preparer to assign scores to mappings, where each mapping represents a way of populating the target from one or more sources
- The target is then populated with data from the highest-scoring mappings.

## Inverting a criterion
Inverting a criterion means that when selecting tuples, those that do not satisfy it will be preferred over those that do. 
> Note: This essentially negates your criterion

## Updating weights
Enter a new value in the weight inputs and click on update weights to change weights.
![Update weights](blob:https://imgur.com/41d64bb2-7c3c-4081-b1c1-ee9b4c010b76)

## How to add a criterion
1. Head over to the **User Context** tab and click on **Add Criterion**.
![User context tab](blob:https://imgur.com/c5d137c1-91f7-4de3-b41c-92cc6ae46f60)

2. A modal to add a criterion will appear. Select the criteria, element and weight.
![Add criterion](https://i.imgur.com/R9hchjL.png)

## Supported criteria
### No parameters required
- completeness wrt. empty values: the ratio of the values that are null or empty over the total number of values
- completeness wrt. tuples: the ratio of the tuples with non-empty values over the total number of tuples. It can only be evaluated on a table
- type numeric: the ratio of the values that represent numbers over the total number of values
- type datetime: the ratio of the values that represent dates or times over the total number of values
- is email: the ratio of the values that represent emails over the total number of values
- is URI:  the ratio of the values that represent URIs over the total number of values
- contain numbers: the ratio of the values that contain a number over the total number of values
- contain letters: the ratio of the values that contain a letter over the total number of values
- contain punctuations: the ratio of the values that contain a punctuation character over the total number of values.
> Note: punctuation is any character that is not a letter or a number or whitespace
- contain email: the ratio of the values that contain an email address over the total number of values
- contain URI: the ratio of the values that contain a URI over the total number of values

### Data context required
- completeness wrt. data context: the ratio of the values included in the Master or Example data over the total number of values
- consistency wrt. data context: the ratio of the values included in the Reference or Example data over the total number of values

### Feedback required
- relevance wrt. feedback: the ratio of the values marked as relevant over the total number of values