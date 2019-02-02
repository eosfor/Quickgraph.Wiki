# Strongly Connected Components

A _strongly connected component_ of a graph is a set of vertices such that for each pair `u,v` of vertices in the component, there exists a path from `u` to `v` and `v` to `u`.

This algorithm sorts the vertices in the different strongly connected components of the graph. It is implemented by the `StronglyConnectedComponentsAlgorithm` which uses the `DepthFirstSearchVertexAlgorithm` internally. Again, `AlgorithmExtensions` contains extension methods that hides these implementation details for you. 

The concept of strong connectivity is very important in many algorithms because it means there is always “a way back”. For example, one expects that the directed graph that represent the different states of a dialog window is strongly connected, i.e. the user can always go back or undo. 

This sample shows how to compute and display the component information from a directed graph:

```csharp
IVertexListGraph<Vertex,Edge> g=…;
IDictionary<Vertex,int> components=new Dictionary<Vertex,int>();

int componentCount = g.StronglyConnectedComponents(components);
if (componentCount!=0)
{
    Console.WriteLine(“Warning the graph is not strongly connected”);
    foreach(KeyValuePair<Vertex,int> kv in components)
        Console.WriteLine(“{0}-{1}”,kv.Value,kv.Key);
}
```
