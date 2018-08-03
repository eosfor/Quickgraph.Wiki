### BidirectionalMatrixGraph

The {{BidirectionalMatrixGraph<TVertex, TEdge>}} provides an efficient data structure to access the out edges and the in edges of a vertex of dense directed graphs with known number of vertices. This class is mutable, serializable, cloneable and [can be constructed in many different ways](Creating-Graphs). Internally, the data structure keeps a 2D fixed size array of edges. Does not support [multi-edges](Multi-Edge).

{{
int vertexCount = ...; // must be known a-priori
var graph = new BidirectionalMatrixGraph<int, Edge<int>>(vertexCount);
...
foreach(var vertex in graph.Vertices)
    foreach(var edge in graph.InEdges(vertex))
        Console.WriteLine(edge);
}}

For sparse graphs, consider using [AdjacencyGraph](AdjacencyGraph) or [BidirectionalGraph](BidirectionalGraph).

