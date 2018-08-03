# **MsAgl is no longer supported!**

#### Visualization Using MsAgl

QuickGraph supports [MsAgl](MsAgl) to render the graphs. The {{QuickGraph.MsAgl}} assembly contains specialize 'populator' that convert a QuickGraph graph into a MsAgl graph.

{{
IVertexAndEdgeListGraph<string, Edge<string>> g = ...;

var populator = MsAglGraphExtensions.CreateMsaglPopulator<string, Edge<string>>(g);
populator.Compute();
Graph g = populator.GleeGraph; // we have the graph :)
}}

Once you have the Glee graph, you can use the MsAgl rendering support or built-in visualizer controll to view it.

##### Customizing the vertices look

Hook to the {{VertexAdded}}, {{EdgeAdded}} events to get a hold on the MsAgl nodes and edges as they are created.

**WARNING: You must have a copy of MsAgl in order to get this to work!**