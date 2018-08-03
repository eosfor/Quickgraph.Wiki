#### Representations

QuickGraph provides various data structures that can represent directed/undirect dense/sparse graphs. All data structures are serializable, cloneable and **not** thread safe. Graphs are mutable or immutable (immutable graphs usually have a more compact representation). The delegate based graphs can be used to keep the memory consumption low.

* Directed graphs
	* [AdjacencyGraph](AdjacencyGraph) provides access to vertices, edges and out edges of sparse directed graphs.
	* [BidirectionalGraph](BidirectionalGraph) extends AdjacencyGraph by providing access to in edges but it requires the double of memory space.
	* [BidirectionalMatrixGraph](BidirectionalMatrixGraph) represented by an array. Efficient for dense directed graphs with known number of vertices.
	* [ArrayAdjacencyGraph](ArrayAdjacencyGraph) and [ArrayBidirectionalGraph](ArrayBidirectionalGraph) are readonly equivalent of [AdjacencyGraph](AdjacencyGraph) and [BidirectionalGraph](BidirectionalGraph). They also use slightly less memory.
	* [CompressedSparseRowGraph](CompressedSparseRowGraph) is an adjacency graph using a compact representation called [compressed sparse row](http://www.cs.utk.edu/~dongarra/etemplates/node373.html). Only the vertex can be of custom type.
	* [DelegateImplicitGraph](DelegateImplicitGraph) wraps the [IImplicitGraph](IImplicitGraph) interface on top of a delegate that a vertex to a set of out vertices. This representation is efficient for large graph that cannot be stored in memory at once 
	* [DelegateIncidenceGraph](DelegateIncidenceGraph) wraps the [IIncidenceGraph](IIncidenceGraph) interface, and extends [DelegateImplicitGraph](DelegateImplicitGraph)
	* [DelegateVertexAndEdgeListGraph](DelegateVertexAndEdgeListGraph) wraps the [IVertexAndEdgeListGraph](IVertexAndEdgeListGraph), extends the DelegateIncidenceGraph, and also uses an enumeration for the vertices
* Undirected graphs
	* [UndirectedGraph](UndirectedGraph) provides a representation for sparse undirected graphs.
* Adapters
	* [BidirectionalAdapterGraph](BidirectionalAdapterGraph) wraps an adjacency graph into a [bidirectional graph](BidirectionalGraph) (access to in-edges)
	* [UndirectedBidirectionalGraph](UndirectedBidirectionalGraph) wraps a bidirectional graph into a [undirected graph](UndirectedGraph).