# Profile Component

## How it works
- Candidate Keys: A candidate key is a collection of attributes, the values of which uniquely identify a row (i.e., there are not two rows with identical values for those attributes). In Data Preparer, candidate key information informs what type of join operation is used to combine tables.


- Inclusion Dependencies: Inclusion dependencies describe overlaps between the values in the attributes of columns in sources. In Data Preparer, inclusion dependencies are used to identify where there is an opportunity to join two tables.

## Example
In the figure below, it is indicated that the values inGoodread.details are contained within those of RainforestBooks.title, with an overlap of 0.667. This indicates that 66.7% of the values in Goodread.details can be found in RainforestBooks.title. Note that this notion of overlap is not symmetrical, and we can also see that the reverse overlap (i.e. the fraction of values in RainforestBooks.title that are also contained in Goodread.details is only 0.278).

![inclusion-deps](https://i.imgur.com/DrslRCx.png)

## Configurations in the control panel
![profiling-config](https://i.imgur.com/5ra1ubM.png)

Profiling parameters configure the discovery of candidate keys and the discovery of inclusion dependencies. 

#### Candidate key discovery parameters
- **Detect candidate keys**: whether to search for candidate key attributes or not. This is enabled by default.
- **Max candidate key size**: the maximum number of attributes that can be used in a candidate key. We recommend this is kept quite low (e.g. 1), as the number of candidate keys in tables with many attributes can grow rapidly

#### Inclusion dependency discovery parameters
- **Overlap threshold**: only inclusion dependencies with at least this fraction of overlap will be used in joins. Note that inclusion dependencies are kept when the overlap in either direction exceeds the overlap threshold.
- **Matches only**: Restrict inclusion dependency discovery only to source tables that have at least one attribute matching an end product attribute.
- **Candidate keys only**: Restrict inclusion dependency discovery only to attributes that are candidate keys.

> Note: These latter two parameters can be used to reduce the number of inclusion dependencies retained, to those that are most relevant to the wrangling task at hand.

## Excluding an inclusion dependency
It is possible to exclude an inclusion dependency or a candidate key in the explain window for the profiling component. As with the matches component, the exclude column can be used to toggle the availability of the inclusion dependency or candidate key in the wrangling process. 

![steering-profiling](https://i.imgur.com/WNEf8tw.png)

In Data Preparer, inclusion dependencies are used in mapping generation to identify when joins can be carried out, so excluding an inclusion dependency means that the attributes in the dependency will not be joined. Similarly, candidate keys are used in mapping generation to determine which attributes are used to join tables, and which join operator to use. As a result, excluding a candidate key will reduce the likelihood that the attributes involved in the key will participate in join conditions.