# Repair transducer

## How it works
Repair Rules: A repair rule uses data context data to fill in gaps in source data. Repair rules are based on functional dependencies, of the form (**determinant** → **dependent**). 
A functional dependency indicates that a value for the determinant uniquely identifies a value for the **dependent**. 

## An example
In Data Preparer, functional dependencies are inferred from the data context as shown in the image. In practice, whenever the attributes in a functional dependency found in the data context can be aligned with attributes in a data set, missing values for the **dependent** attribute in the data set can be replaced with the corresponding value from the data context.

![Repair transducer output](https://i.imgur.com/huf8gN9.png)

 For example, the dependency (**MasterData.title** → **MasterData.rating**) can be used to populate missing values for **rating** in **Riverside** books, and we can see that 16 values for **Riverside.rating** have been updated using this dependency.


## Configurations in the control panel
![repair-config](https://i.imgur.com/2bKKQrf.png)

#### Format match parameters:
**Apply rules**: Leave the box:
- unchecked in order to verify whether to apply or discard suggested repairs. 
- checked to repair sources directly, based on the discovered rules, in which case you can still view applied repairs.git add



