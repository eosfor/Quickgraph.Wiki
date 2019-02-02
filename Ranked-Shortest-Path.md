# Ranked Shortest Path Algorithm

This is a variation of the [Shortest Path](Shortest-Path) algorithm where not only the first one, but k-th shortest paths are returned

The [Hoffman-Pavlet](http://portal.acm.org/citation.cfm?doid=320998.321004) algorithm provides an implementation this problem for directed weight graph with positive weights.

```csharp
IBidirectionalGraph<TVertex, TEdge> g = ...;
Func<TEdge, double> edgeWeights = ...;
TVertex source = ...;
TVertex target = ...;
int pathCount = 5;

foreach(IEnumerable<TEdge> path in g.RankedShortestPathHoffman(g, edgeWeights, source, target, 5))
    ...
```
