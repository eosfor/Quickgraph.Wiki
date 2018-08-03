#### Mutation concepts

The **mutation concepts** define the different ways a graph can be modified. The hierarchy of mutation interface duplicates the traversal hierarchy and adds functionality to mutate the graph.

* {{IMutableGraph}} defines a graph that can be cleared,
* {{IMutableIncidenceGraph}} defines methods to remove out-edges,
* {{IMutableVertexListGraph}} defines methods to add and remove vertices,
* {{IMutableEdgeListGraph}} defines methods to add and remove edges
* {{IMutableVertexAndEdgeListGraph}} merges the two above concepts,
* {{IMutableBidirectionalGraph}} defines method to remove out-edges
