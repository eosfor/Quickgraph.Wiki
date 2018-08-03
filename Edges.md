### Edges

While a vertex could be any type with QuickGraph, the edge type must implement {{IEdge<TVertex>}} (and comply to it's contract). QuickGraph comes with various default implementations:
* classes
	* {{Edge<TVertex>}}, an vanilla implementation,
	* {{EquatableEdge<TVertex>}}, implements {{IEquatable<EquatableEdge<TVertex>>}},
	* {{TaggedEdge<TVertex,TTag>}}, holds a tag,
	* {{TaggedEquatableEdge<TVertex,TTag>}}, equatable and holds a tag,
* structs
	* {{SEdge<TVertex>}}, an immutable edge,
	* {{SEquatableEdge<TVertex>}}, a struct that implements {{IEquatable<SEquatableEdge<TVertex>>}},
	* {{STaggedEdge<TVertex, TTag>}}, holds a tag
	* {{STaggedEquatableEdge<TVertex,TTag>}}, equatable and holds a tag,

The struct based edge will provide better performance and should be used when you do not plan to use custom edges. Of course, you can always implement your own version {{IEdge<TVertex>}}. Tagged edges also implement {{ITagged<TTag>}}. 

#### Undirected edges

In undirected graphs, the order of the source or target vertices should not matter. In order to improve efficiency, edges that implement the {{IUndirectedEdge<TVertex>}} interface must sort the vertices so that {{Source <= Target}} (with respect to the default Comparer). This provides some performance gains in various data structures and algorithms. 
* classes
	* {{UndirectedEdge<TVertex>}}, an vanilla implementation,
	* {{TaggedUndirectedEdge<TVertex,TTag>}}, holds a tag,
* structs
	* {{SUndirectedEdge<TVertex>}}, an immutable edge,
	* {{STaggedUndirectedEdge<TVertex, TTag>}}, holds a tag
