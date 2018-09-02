#### Visualization Using GLEE

QuickGraph supports [Glee](Glee) to render the graphs. The `QuickGraph.Glee` assembly contains specialize 'populator' that convert a QuickGraph graph into a Glee graph.

```
IVertexAndEdgeListGraph<string, Edge<string>> g = ...;

var populator = GleeGraphExtensions.Create<string, Edge<string>>(g);
populator.Compute();
Graph g = populator.GleeGraph; // we have the graph :)
```

Once you have the Glee graph, you can use the Glee rendering support or built-in visualizer controll to view it.

##### Customizing the vertices look

Hook to the `VertexAdded`, `EdgeAdded` events to get a hold on the GLEE nodes and edges as they are created.

**WARNING: You must download and copy the Glee assemblies in order to get this to work!**