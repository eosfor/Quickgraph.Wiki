# Floyd Warshall All Path Shortest Path

The [Floyd Warshall All Path Shortest Path](http://en.wikipedia.org/wiki/Floyd-Warshall_algorithm) finds all the shortest path in a weighted, directed path. It can also be used to detect negative cycles.

```csharp
var g = ... ; // some graph of TVertex, TEdge
var weights = ... ; // a function that maps TEdge -> double
var fw = new FloydWarshallAllShortestPathAlgorithm<TVertex, TEdge>(g, weights);

// compute
fw.Compute();

// get interresting paths,
foreach(var source in g.Vertices)
    foreach(var target in g.Vertices)
    {
        IEnumerable<TEdge> path;
        if(fw.TryGetPath(source, target, out path)
            foreach(var edge in path)
                Console.WriteLine(edge);
    }
```
