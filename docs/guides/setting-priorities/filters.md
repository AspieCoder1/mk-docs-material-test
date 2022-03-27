# Selecting Results using Criteria

## How it works
- The **User Context** contains a collection of criteria, each identifying a feature of the result that is important to the user. 
 - Each criterion has a weight set by the user. This is used to indicate the importance of criteria compared to each other. 
- These criteria are used by Data Preparer to assign scores to mappings, where each mapping represents a way of populating the target from one or more sources
- The target is then populated with data from the highest-scoring mappings.

## Inverting a filter
Inverting a filter means that only tuples which do not satisfy the filter will be allowed to populate the end product. 
> Note: This essentially negates your filter.

## How to add a filter
1. Head over to the **User Context** tab and click on **Add filter**.
![User context tab](blob:https://imgur.com/6987aa36-2a3b-4d8a-9f0c-5519b9134ac4)

2. A modal to add a filter will appear. Select your filter and element.
![Add Filter](blob:https://imgur.com/14e3d1a2-ab82-4465-a0f4-e1c7b18d9b29)

## Supported filters
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