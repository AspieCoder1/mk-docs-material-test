# Match
<!-- TODO: fixup -->
This section lists associations that have been identified between source and target attributes. The presence of a match indicates that Data Preparer considers the source attribute as a plausible source of values for the target attribute. In the example, GoodRead.details has been matched with BookPromotions.title, with a similarity score of 0.532. These attributes have been matched because, although the attribute names are different, their values are similar. The score is in the range 0 to 1, where the higher the score the more similar they are deemed to be. Matches are used in Data Preparer to identify which source attributes can be used to populate which target attributes, and to identify tables that, when used together, may be able to populate more target attributes than they can alone.

Candidate Keys: A candidate key is a collection of attributes, the values of which uniquely
identify a row (i.e., there are not two rows with identical values for those attributes). In
Data Preparer, candidate key information informs what type of join operation is used to
combine tables.

Inclusion Dependencies: Inclusion dependencies describe overlaps between the values in
the attributes of columns in sources. For example, in Figure 18, it is indicated that the values inGoodread.details are contained within those of RainforestBooks.title, with an overlap
of 0.667. This indicates that 66.7% of the values in Goodread.details can be found in RainforestBooks.title. Note that this notion of overlap is not symmetrical, and we can also see
that the reverse overlap (i.e. the fraction of values in RainforestBooks.title that are also
contained in Goodread.details is only 0.278). In Data Preparer, inclusion dependencies
are used to identify where there is an opportunity to join two tables.