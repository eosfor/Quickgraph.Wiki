### AdjacencyGraph

The `AdjacencyGraph<TVertex, TEdge>`, also known as [adjacency list](http://en.wikipedia.org/wiki/Adjacency_list) provides an efficient data structure to access the out edges of a vertex. This class is mutable, serializable, cloneable and [can be constructed in many different ways](Creating-Graphs). Internally, the data structure keeps a dictionary from TVertex to a unordered list of TEdge elements.

```
var graph = new AdjacencyGraph<int, Edge<int>>();
...
foreach(var vertex in graph.Vertices)
    foreach(var edge in graph.OutEdges(vertex))
        Console.WriteLine(edge);
```

If you need to access in-edges as well, consider using the [BidirectionalGraph](BidirectionalGraph).

