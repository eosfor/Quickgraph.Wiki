#### Maximum Bipartite Matching

The [Maximum Bipartite Matching Algorithm](http://en.wikipedia.org/wiki/Matching_(graph_theory)#Maximum_matchings_in_bipartite_graphs) problem arises in many real world situations.  
It is currently implemented by [transforming the input graph](http://en.wikipedia.org/wiki/Maximum_flow_problem#Maximum_cardinality_bipartite_matching) to a maximum flow graph, and then using the MaximumFlowEdmondsKarp algorithm

{{
// we need a graph and two sets of vertices
IMutableVertexAndEdgeListGraph<TVertex,TEdge> graph = ...;

// sets a and b must be distinct, and their union must be equal to the set of all vertices in the graph
IEnumerable<TVertex> vertexSetA = ...;
IEnumerable<TVertex> vertexSetB = ...;

// These functions used to create new vertices and edges during the execution of the algorithm.  
// All added objects are removed before the computation returns
VertexFactory<TVertex> vertexFactory = <some method which creates a new TVertex>;
EdgeFactory<TVertex, TEdge> edgeFactory = (source, target) => new Edge<TVertex>(source,target);


// computing the maximum bipartite match
var maxMatch = new MaximumBipartiteMatchingAlgorithm<TVertex, TEdge>(
        graph, vertexSetA, vertexSetB, vertexFactory, edgeFactory);

// Use the MatchedEdges property to access the computed maximum match
ProcessResult(maxMatch.MatchedEdges);

}}