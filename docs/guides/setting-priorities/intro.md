# Setting Priorities

## Motivation
By default, Data Preparer takes responsibility for exploring the space of data preparation options. These options may represent different data sources, some of which may provide better quality or more relevant data than others, and different ways of wrangling this data, which again may be more or less suitable for the task in hand. 

Often there may be trade-offs.
> Example: Obtaining a larger result from the wrangling process may involve certain compromises in relation to quality. 

> Data scientists also face these trade-offs in manual data preparation.

## User context feature
In Data Preparer, a user can select data that meets their specified priorities by configuring their data priorities through the **User Context** tab.
There are 2 methods to set the priorities, through using **Criteria** and through using **Filters**, which will be discussed in the next section.

### Criteria and Filters
- **Criteria** are set to compare tuples and choose the better tuples by their weight
- **Filters** are set to exclude values that are not suitable for the analysis

> Note: Filters are applied after criteria are applied, and thus can lead to smaller results than requested as the product size.