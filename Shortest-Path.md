# Shortest Path

This **single source shortest path** can be expressed as follows: given a weighted directed graph, find the minimum path between a vertex `u` and  any other vertex `v`.

Depending on the properties of the weights and the graph, different algorithms can be applied:

* positive weights, a graph is a [Directed Acyclic Graph](http://en.wikipedia.org/wiki/Directed_acyclic_graph): [DagShortestPathAlgorithm](DagShortestPathAlgorithm),
* positive weights: [DijsktraShortestPathAlgorithm](DijsktraShortestPathAlgorithm),
* positive weights, with heuristics: [AStartShortestPathAlgorithm](AStartShortestPathAlgorithm),
* positive or negative weights:  [BellmanFordShortestPathAlgorithm](BellmanFordShortestPathAlgorithm)

## Quick example

The [AlgorithmExtensions](AlgorithmExtensions) contains extension methods to compute the shortest path without the ugly details.

```csharp
IVertexAndEdgeListGraph<int, Edge<int>> cities = ...; // a graph of cities
Func<Edge<int>, double> cityDistances = ...; // a delegate that gives the distance between cities

int sourceCity = 0; // starting city
int targetCity = 0; // ending city

// vis can create all the shortest path in the graph
// and returns a delegate that can be used to retrieve the graphs
TryGetFunc<int, IEnumerable<int>> tryGetPath = cities.ShortestPathsDijkstra(cityDistances, sourceCity);
// enumerating path to targetCity, if any
IEnumerable<Edge<int>> path;
if (tryGetPath(targetCity, out path))
    foreach (var e in path)
        Console.WriteLine(e);
```

## Full example

This sample shows how to compute the shortest path between different cities.

```csharp
// creating the algorithm instance
var dijkstra =
    new DijkstraShortestPathAlgorithm<int,Edge<int>>(cities, cityDistances);

// creating the observer
var vis = new VertexPredecessorRecorderObserver<int,Edge<int>>();

// compute and record shortest paths
using(ObserverScope.Create(dijkstra, vis))
   dijkstra.Compute(sourceCity);

// vis can create all the shortest path in the graph
foreach(var e in vis.Path(targetCity))
   Console.WriteLine(e);  
```