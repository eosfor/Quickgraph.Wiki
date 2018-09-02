### Minimum Spanning Tree

Finding the [minimum spanning tree](http://en.wikipedia.org/wiki/Minimum_spanning_tree) of an weighted undirected graph is a fundamental problem that applies to many areas. QuickGraph provides 2 implementations to solve this problem: [Prim's](http://en.wikipedia.org/wiki/Prim%27s_algorithm) and [Kruskal's](http://en.wikipedia.org/wiki/Kruskal%27s_algorithm).

* Prim's algorithm is based on Dijkstra shortest path. This algorithm is implemented as an extension method in [AlgorithmExtensions](AlgorithmExtensions). This method returns a sequence of edges that represent the tree.
```
    IUndirectedGraph<TVertex, TEdge> g = ...;
    Func<TEdge, double> edgeWeights = ...;
    IEnumerable<TEdge> mst = g.MinimumSpanningTreePrim(g, edgeWeights);
```
* Kruskal's algorithm is based on disjoint-sets. This algorithm can be invoked similarly to `MinimumSpanningTreePrim`.
```
    IEnumerable<TEdge> mst = g.MinimumSpanningTreeKruskal(g, edgeWeights);
```