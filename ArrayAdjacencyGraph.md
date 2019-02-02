# ArrayAdjacencyGraph

The ```ArrayAdjacencyGraph<TVertex, TEdge>```, also known as [adjacency list](http://en.wikipedia.org/wiki/Adjacency_list) provides an efficient  **readonly** data structure to access the out edges of a vertex. This class is serializable, cloneable and [can be constructed in many different ways](Creating-Graphs.md). Internally, the data structure keeps a dictionary from TVertex to an unordered array of TEdge elements.

See also [AdjacencyGraph](AdjacencyGraph.md).