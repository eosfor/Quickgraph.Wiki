# BidirectionalGraph

The ```BidirectionalGraph<TVertex, TEdge>``` provides an efficient data structure to access the out edges and the in edges of a vertex of sparse directed graphs. This class is mutable, serializable, cloneable and [can be constructed in many different ways](Creating-Graphs). Internally, the data structure keeps a dictionary from TVertex to a unordered list of TEdge elements.

```csharp
var graph = new BidirectionalGraph<int, Edge<int>>();
...
foreach(var vertex in graph.Vertices)
    foreach(var edge in graph.InEdges(vertex))
        Console.WriteLine(edge);
```

If you only need to access out-edges, consider using the [AdjacencyGraph](AdjacencyGraph.md), as it uses half the memory.