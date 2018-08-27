### Condensation Graph

This algorithm condensate any graph by merge a set of edges in a _condensated edge_. The user can provide a predicate of edges to specify which edge to condensate or condenstate by components as well.

The [AlgorithmExtensions](AlgorithmExtensions) class provide various helpers, `Condensate...`, to condenstate graphs:
```
IVertexAndEdgeListGraph<TVertex, TEdge> g = ...; // input graph
var condensated = g.CondenstateWeaklyConnected();
```