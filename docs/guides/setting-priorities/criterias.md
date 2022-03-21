# Prioritizing Results using Criteria

## How it works
- The **User Context** contains a collection of criteria, each identifying a feature of the result that is important to the user. 
- Each criterion has a weight which is set by the user, that is used to indicate how important the criteria are compared to each other. 
- These criteria are used by Data Preparer to assign scores to mappings, where each mapping represents a way of populating the target from one or more sources
- The target is then populated with data from the highest scoring mappings.

## Inverting a criterion
Inverting a criterion means that when selecting tuples, the ones that do not satisfy the criterion will be preferred over the ones that satisfy the criterion. 
> Note: This is essentially putting a putting a "not" in front of your criterion

## Updating weights
If you feel the need to change the weights, simply enter a new value in the weight inputs and click on update weights.
![Update weights](blob:https://imgur.com/41d64bb2-7c3c-4081-b1c1-ee9b4c010b76)

## How to add a criterion
1.  Head over to the **User Context** tab and click on **Add Criterion**.
![User context tab](blob:https://imgur.com/c5d137c1-91f7-4de3-b41c-92cc6ae46f60)

2. A modal to add a criterion will appear. Select your criterion, element and weight.
![Add criterion](https://i.imgur.com/R9hchjL.png)

## Supported criteria
### No parameters required
- completeness wrt. empty values: the ratio of the values that are null or empty over the total number of values
- completeness wrt. tuples: the ratio of the tuples with non-empty values over the total number of tuples. Can only be evaluated on a table
- type numeric: the ratio of the values that represent numbers over the total number of values
- type datetime: the ratio of the values that represent dates or times over the total number of values
- is email: the ratio of the values that represent emails over the total number of values
- is uri:  the ratio of the values that represent uris over the total number of values
- contain numbers: the ratio of the values that contain a number over the total number of values
- contain letters: the ratio of the values that contain a letter over the total number of values
- contain punctuations: the ratio of the values that contain a punctuation character over the total number of values.
> Note: punctuation is any character that is not a letter or a number or whitespace
- contain email: the ratio of the values that contain an email address over the total number of values
- contain uri: the ratio of the values that contain a uri over the total number of values

### Data context required
- completeness wrt. data context: the ratio of the values included in the Master or Example data over the total number of values
- consistency wrt. data context: he ratio of the values included in the Reference or Example data over the total number of values

### Feedback required
- relevance wrt. feedback: the ratio of the values marked as relevant over the total number of values