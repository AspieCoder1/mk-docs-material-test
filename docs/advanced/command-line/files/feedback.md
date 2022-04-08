# Feedback
This file describes the feedback instances, one feedback instance per line. 

## Format of the file
We have provided an example of how the contents of the file should be structured in **feedback.csv** in the Manual Books example.

### Headers
The headers in this file should match the names and the order of the fields of the target schema, as defined in the property product.fields(see [Wrangle Properties](../commands.md)). 

### Columns
Then, an additional column header is expected, titled relevant. 

- Positive values in this column (any of: yes, y, 1, true, or t) indicate that the values in the feedback instance are relevant. 
- If more than one value is filled in a CSV line, then the line is considered to be tuple-level feedback. 
- If only one value is present, then the line is considered to be attribute-level feedback.