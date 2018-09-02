#### Traversal Concepts

The **traversal concepts** define the different way the vertices and edges of a graph can be accessed and enumerated. 

* _Tip:_ All the interfaces depend on 2 generic parameters `TVertex` and `TEdge`, where `TEdge` has the additional constraint of implementing `IEdge<TVertex>`.

Each of these interfaces is described below (generic arguments have been omitted for the sake of clarity):

* `IImplicitGraph` defines a graph that contains information about the out-edges of a vertex. This interface is particularly important when the size of your graph is infinite and you only have “local information”,
* `IIncidenceGraph` extends IImplicitGraph by providing the out-edges count,
* `IVertexListGraph` defines a graph that publishes the collection of vertices. With this concept, one can iterate the vertices and access the out edges of each vertex. This is an important concept that is used by many algorithms.
* `IEdgeListGraph` defines a graph that publishes the collection of edges. No information about out-edges is available.
* `IVertexAndEdgeListGraph` merges IVertexListGraph and IEdgeListGraph functionalities
* `IBidirectionalGraph` defines a vertex list graph that also publishes the in-edges. Such graph can be used to explore a graph in a both directions.

![](Traversal Concepts_TraversalInterfaces.png)