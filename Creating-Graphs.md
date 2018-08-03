#### Creating Graphs

##### Easy creation with extension methods
QuickGraph provides several extension methods in {{QuickGraph.GraphExtensions}} to create graph from list of edge or vertices. For example, from an {{IEnumerable<Edge<int>>}}:
{{
using QuickGraph; // enables extension methods

var edges = new SEdge<int>[]() { new SEdge<int>(1,2), new SEdge<int>(0,1) };
var graph = edges.ToAdjacencyGraph<int, SEdge<int>>(edges);
}}

##### Create a graph instance
Let us assume we need integer vertices and edges tagged with string. Int is the vertex type and we can use the MarkedEdge generic type for the edge type:
* {{TVertex}} type: {{int}}
* {{TEdge}} type using {{TaggedEdge<Vertex,Marker>: TaggedEdge<int, string>}}
{{
var g = new AdjacencyGraph<int, TaggedEdge<int, string>>();
}}

##### Wrapping a dictionary into a graph
You may have already a dictionary on hand that represents a graph, where the keys are the vertices and the value is a collection of out-edges (or adjacent edges). You can wrap this dictionary with QuickGraph without re-allocating new memory:
{{
Dictionary<int, int[]()> dic = ...; // vertex -> target edges
var graph = dic.ToVertexAndEdgeListGraph(
    kv => Array.ConvertAll(kv.Value, v => new SEquatableEdge<int>(kv.Key, v))
    );

-- without extension methods
var graph = GraphExtensions.ToVertexAndEdgeListGraph(
    dic,
    kv => Array.ConvertAll(kv.Value, v => new SEquatableEdge<int>(kv.Key, v))
    );
}}

##### Adding vertices
This snippet creates two vertices and adds them to the graph.
{{
int v1 = 1;
int v2 = 2;

g.AddVertex(v1);
g.AddVertex(v2);
}}
##### Adding edges
The edges {{(v1,v2)}} and {{(v2,v1)}} are created and added to the graph.
{{
var e1 = new TaggedEdge<int,string>(v1,v2,”hello”);

g.AddEdge(e1); 
}}
##### Adding edges (and vertices)
You can also add an edge and implicitely add the vertices if they are missing
{{
// v3, v4 are not added to the graph yet
var e2 = new TaggedEdge<int,string>(v3,v4,”hello”);

g.AddVerticesAndEdge(e2); 
}}
