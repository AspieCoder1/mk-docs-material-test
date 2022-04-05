# Match transducer

## How it works
It is the first transducer in the workflow. This transducer lists associations that have been identified between source and target attributes. The presence of a match indicates that Data Preparer considers the source attribute as a plausible source of values for the target attribute. 

![Workflow order](https://i.imgur.com/K0BfQiM.png)

Matches are used in Data Preparer to identify which source attributes can be used to populate which target attributes, and to identify tables that, when used together, may be able to populate more target attributes than they can alone.

## An example
In the example, using *ManualBook1.scenario*, GoodRead.details has been matched with BookPromotions.title, with a similarity score of 0.532 as seen in the first row. 
![Match Transducer output](https://i.imgur.com/d2KJWGd.png)

These attributes have been matched because, although the attribute names are different, their values are similar. The score is in the range 0 to 1, where the higher the score the more similar they are deemed to be. 

## Configurations in the control panel
![match-config](https://i.imgur.com/XvcE8JB.png)

#### Format match parameters:
- **match strategy**: Here there are three options: schema, schema+instances and instances. 

- Schema is where only the attribute names will be compared for similarity.
- Schema+Instances is where both attribute and instances will be compared for similarity
- Instances is where only attribute instances will be compared for similarity.

- **match threshold**: This is a number between 0 and 1 that defines the threshold below which all matches will be discarded.

- **match instances max**: This is the number of instances to compare when evaluating similarity between two attributes.
>Note: Set to 0 for unlimited.



