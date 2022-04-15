# Custom no op transducer

In previous parts of the documentation, a trasducers has been discribed as a step in a data processing pipeline.
It takes in some data as well as settings and combines these together to create a new data source.
This page describes how to make the most basic custom transducer, the *no-op transducer*.
This is the transducer which performs no actions on the data.

## Trasducer implementation
The following UML diagram demonstrates a custom transducer implementation, this can be generalised to the existing transducers:
![Custom transducer UML](https://i.imgur.com/0OtGpaA.png){.center}