### Incremental Connected Components

This algorithm maintains a set of connected components for growing graphs (added edges only). Under the hood, it uses a [disjoint set](http___en.wikipedia.org_wiki_Disjoint-set_data_structure) data structure to keep track of the components.

The {{AlgorithmExtensions.IncrementConnectedComponents}} returns a delegate that returns the update component count and map on each call. The delegate is a {{Func<KeyValuePair<int, IDictionary<TVertex, int>>}} where {{Key}} is the component count and {{Value}} is the map of vertices to component index.
{{
var g = new AdjacencyGraph<int, SEdge<int>>();
g.AddVertexRange(new int[]() { 0, 1, 2, 3 });
Func<KeyValuePair<int, IDictionary<TVertex, int>> components = AlgorithmExtensions.IncrementalConnectedComponents(g);

var current = components();
Assert.AreEqual(4, current.Key);

g.AddEdge(new SEdge<int>(0, 1));
current = components(); // query algorithm again
Assert.AreEqual(3, current.Key);
}}

See also [Boost documentation on this algorithm](http___boost.sourceforge.net_libs_graph_doc_incremental_components.html).