# Condensation Graph

This algorithm condensate any graph by merge a set of edges in a _condensed edge_. The user can provide a predicate of edges to specify which edge to condensate or condense by components as well.

The [AlgorithmExtensions](AlgorithmExtensions.md) class provide various helpers, ```Condensate...```, to condense graphs:

```csharp
IVertexAndEdgeListGraph<TVertex, TEdge> g = ...; // input graph
var condensated = g.CondenstateWeaklyConnected();
```