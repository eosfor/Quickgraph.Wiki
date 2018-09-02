#### Observers Concepts

Algorithms do not serialize any interesting data. They publish a set of standard events that an observer can listen to gather the data (algorithms and observers in QuickGraph implement the [Observer Pattern](Observer-Pattern)). For example, one can attach an observer that records the vertex predecessors to algorithms that compute the shortest path.

* `VertexPredecessorRecorderObserver`, creates a dictionary that links vertices to their parent edge,
* `EdgePredecessorRecorderObserver`, create a dictionary that links vertices to their parent edge,
* `VertexDistanceRecorderObserver`, stores the distance of vertices from the root vertex,
* `VertexTimeStamperObserver`, stores the time instant where a vertex processing start and finishes
 
##### Using observers

Observer instance are to be 'attached' to algorithms during the computation. All observer implement an `Attach` method that returns a disposable instance. When disposing, this instance 'detached' the observer from the algorithm events.

```
    IVertexListGraph<TVertex,TEdge> g = ...; // some graph instance
    var dfs = new DepthFirstSearchAlgorithm<TVertex,TEdge>(g);
    var predecessorRecorder = new VertexPredecessorRecorderObserver<TVertex,TEdge>();

    using(predecessorRecorder.Attach(dfs)) // listen to dfs events, then unhook
        dfs.Compute();   
```
