# **MSAGL is no longer supported!** (TODO: need some clarification here, as MSAGL is GLEE?)

## Visualization Using MSAGL

QuickGraph supports [MSAGL](MsAgl) to render the graphs. The `QuickGraph.MsAgl` assembly contains specialize 'populator' that convert a QuickGraph graph into a MSAGL graph.

```csharp
IVertexAndEdgeListGraph<string, Edge<string>> g = ...;

var populator = MsAglGraphExtensions.CreateMsaglPopulator<string, Edge<string>>(g);
populator.Compute();
Graph g = populator.GleeGraph; // we have the graph :)
```

Once you have the Glee graph, you can use the MSAGL rendering support or built-in visualizer control to view it.

## Customizing the vertices look

Hook to the `VertexAdded`, `EdgeAdded` events to get a hold on the MSAGL nodes and edges as they are created.

**WARNING: You must have a copy of MSAGL in order to get this to work!**