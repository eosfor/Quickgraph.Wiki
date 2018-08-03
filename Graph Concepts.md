#### Concepts

Often, algorithms have different requirement. Some will need to iterate all the vertices while other need to access the out edges, etc… The subset of functionalities that each algorithm requires is often identified as a graph concept: 

* A **graph concept** defines the functionality required by a family of algorithms. 

As functionality always comes with a price (there’s no free lunch), it is important to have a fine grained structure of graph concepts that let the algorithm writer pick just what he needs and no more. In C#, a graph concept translates naturally and elegantly to interfaces. Therefore in the following, we will use interface or concept without distinction.

There are two main families of graph concepts in QuickGraph: 
* [Traversal Concepts](Traversal-Concepts) 
* [Mutation Concepts](Mutation-Concepts)

Graph concepts have been introduced by the [Boost Graph Library](Boost-Graph-Library) authors and the design of QuickGraph follows their design.
