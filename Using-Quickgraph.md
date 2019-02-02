# Using QuickGraph

## Setting up your project

* Add a reference to `QuickGraph.dll` to your project. QuickGraph provides a version backward compatible with .Net 2.0 or a .Net 3.5 version. The only difference lies in the support for extension methods.
* Most data structures are defined under the `QuickGraph` namespace, algorithms are under the `QuickGraph.Algorithms` namespace.

## Identify the vertex and edge types

The vertex type can be any type as all QuickGraph datastructure are generic. The edge type must implement the `IEdge<TVertex>` interface:

```csharp
class FooVertex {} // custom vertex type
class FooEdge : Edge<FooVertex> []() // custom edge type
class FooGraph : AdjacencyGraph<FooVertex, FooEdge> {} // custom graph type
```

## That's it

* You can learn more about [creating graphs](Create-Graphs), [walking graphs](Walking-Graphs) or [mutating graphs](Mutate-Graphs).