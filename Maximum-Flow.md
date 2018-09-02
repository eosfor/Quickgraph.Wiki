#### Maximum Flow

The [Edmond and Karp](http://en.wikipedia.org/wiki/Edmonds-Karp_algorithm) algorithm computes a maximum flow for directed graph with positive capacities and flows. 

```
// we need a graph, a source and a sink
IMutableVertexAndEdgeListGraph<TVertex,TEdge> graph = ...;
TVertex source = ...;
TVertex sink = ...;

// A function with maps an edge to its capacity
Func<TEdge, double> capacityFunc = (edge => 1);

// A function which takes a vertex and returns the edge connecting to its predecessor in the flow network
TryFunc<TVertex, TEdge> flowPredecessors;

// A function used to create new edges during the execution of the algorithm.  These edges are removed before the computation returns
EdgeFactory<TVertex, TEdge> edgeFactory = (source, target) => new Edge<TVertex>(source,target);

// computing the maximum flow using Edmonds Karp.
double flow = AlgorithmExtensions.MaximumFlowEdmondsKarp<TVertex, TEdge>(
    graph,
    capacityFunc,
    source, sink,
    out flowPredecessors,
    edgeFactory);
```