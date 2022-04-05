# Match transducer

## How it works
This transducer lists associations that have been identified between source and target attributes. The presence of a match indicates that Data Preparer considers the source attribute as a plausible source of values for the target attribute. 

Matches are used in Data Preparer to identify which source attributes can be used to populate which target attributes, and to identify tables that, when used together, may be able to populate more target attributes than they can alone.

## An example
In the example, using ManualBooks1.scenario, GoodRead.details has been matched with BookPromotions.title, with a similarity score of 0.532. 

These attributes have been matched because, although the attribute names are different, their values are similar. The score is in the range 0 to 1, where the higher the score the more similar they are deemed to be. 



