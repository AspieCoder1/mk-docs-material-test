# Data Preperation Process
## Motivation
There is no widely accepted data preparation process, and Data Preparer doesn’t impose, or even imply, a particular process. However, the inherent uncertainty associated with data preparation, where the properties of individual sources and the relationships between them are not fully understood up-front, suggests that an iterative process will be standard. 

## The Datapreparer Workflow
Data Preparer might be considered to be well suited to an iterative process, as automation enables rapid rewrangling with additional sources or evidence. Here is a possible mode of operation:

### Iterate the following steps:
- (Re)Define the target: The purpose of the wrangling process is to populate the target. This purpose needs to be made explicit through a definition for the target. This may then be refined, as problems with the proposal or opportunities from the data emerge.
-  Obtain source and data context data sets: Identify data sets that can be used to populate the target, and data context that can be aligned with as many target attributes as possible.
- Wrangle using Data Preparer: Running Data Preparer will produce a result based on the current inputs.
- Review the results: If suitable, then exit the iteration.
- Refine the process:
    - Review explanation of how results were produced: identifying the most suitable next step requires a good understanding of what is possible with the available data, and how Data Preparer is currently wrangling the data. This means reviewing the result and how it was obtained in some detail.
    - Revise the user context: If suitable data is present, but is not being selected, refine the user context to provide a result that fits better with the requirements.
    - Identify new sources or data context to add: if there is insufficient data or insufficient evidence to enable it to be wrangled effectively, consider how to fill these gaps.
    - Revise how Data Preparer is wrangling the data: Change the control parameters, or engage in more detailed steering by changing the results of individual steps or refining how individual sources participate in wrangling