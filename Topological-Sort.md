#### Topological Sort

This algorithm creates an [linear ordering](http://en.wikipedia.org/wiki/Topological_sort) of the vertices (or edges) in a [Directed Acyclic Graph](http://en.wikipedia.org/wiki/Directed_acyclic_graph) such that each vertex comes before its outbound vertices. A typical example of the topological sort is the build dependencies ordering.

The topological sort is simply computed using the {{TopologicalSortAlgorithm}} class, 
which uses the {{DepthFirstSearchVertexAlgorithm}} internaly. 

{{TopologicalSort}} is an extension method of [AlgorithmExtensions](AlgorithmExtensions) to simplify this task:
{{
IVertexListGraph<Vertex,Edge> g;
// iterating over the sorted vertices
foreach(Vertex v in g.TopologialSort())
{…}
}}
QuickGraph contains a second topological sort algorithm that sorts vertices by increasing in-degree such that source vertices are takened first. It is implemented by {{SourceFirstTopologicalSortAlgorithm}} and wrapped by the extension method {{AlgoExtensions.SourceFirstTopologicalSort}}.
