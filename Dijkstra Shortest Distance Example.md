### Dijkstra Shortest Path Distance Example

#### Dijkstra extension methods

The AlgorithmExtensions class contains several helper methods to execute the algorithm on a given graph.
{{
using QuickGraph;
using QuickGraph.Algorithms;

IVertexAndEdgeListGraph<TVertex, TEdge> graph = ...;
Func<TEdge, double> edgeCost = e => 1; // constant cost
TVertex root = ...;

// compute shortest paths
TryFunc<TVertex, TEdge> tryGetPaths = graph.ShortestPathDijkstra(edgeCost, root);

// query path for given vertices
TVertex target = ...;
IEnumerable<TEdge> path;
if (tryGetPaths(target, out path))
    foreach(var edge in path)
        Console.WriteLine(edge);
}}

#### Advanced use
This example sets up a Dijkstra shortest path algorithm and computes the distance of the vertices in the graph.
{{
Func<TEdge, double> edgeCost = e => 1; // constant cost
// We want to use Dijkstra on this graph
var dijkstra = new DijkstraShortestPathAlgorithm<TEdge, TEdge>(graph, edgeCost);
}}
#### Using a predecessor recorder to build the shortest path tree
Algorithms raise a number of events that [observes](Observer-Concepts) can leverage to build solutions. For example, attaching a predecessor recorder
to the Dijkstra algorithm will let us build a predecessor tree. This tree is later used to build shortest paths.
{{
// Attach a Vertex Predecessor Recorder Observer to give us the paths
var predecessors = new VertexPredecessorRecorderObserver<TVertex, TEdge>();
using (predecessors.Attach(dijkstra))
    // Run the algorithm with A set to be the source
    dijkstra.Compute("A");
}}
The {{predecessors}} instance now contains a dictionary of distance from each vertex to the source:
{{
foreach (var v in graph.Vertices) {
    double distance = 0;
    TVertex vertex = v;
    TEdge predecessor;
     while (predecessors.VertexPredecessors.TryGetValue(vertex, out predecessor)) {
          distance += edgeCost[predecessor](predecessor);
          vertex = predecessor.Source;
     }
     Console.WriteLine("A -> {0}: {1}", v, distance);
}
}}
##### Using a dictionary for edge costs
Because the algorithm take a delegate as the edge cost, one cannot simply pass a dictionary. QuickGraph provides a helper method, GetIndexer, to make the conversion:
{{
Dictionary<TEdge, double> edgeCostDictionary = ...
Func<TEdge,double> edgeCost = AlgorithmExtensions.GetIndexer(edgeCostDictionary);
...
}}