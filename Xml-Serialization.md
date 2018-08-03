#### Xml Serialization

QuickGraph supports loading and saving graphs to and from Xml. The implementation builds on top of {{XmlReader}} and {{XmlWriter}} and is located in the {{SerializationExtensions}} class from the {{QuickGraph.Serialization}} namespace.

##### Serializing graphs

To serialize a graph, call the {{SerializeToXml}} extension methods with an {{XmlWriter}} instance and delegates that can map vertices and edges to an identifier string. The serialization method also supports custom delegate to write additional information per vertex, edge.
{{
class MyVertex {
    public int ID { get;set; } 
}
class MyEdge : IEdge<MyVertex> {
    string Name { get; set; }
    string Tag { get; set; }
}
var g = new AdjacencyGraph<MyVexte, MyEdge>();
...
using(var xwriter = XmlWriter.Create(...))
    g.SerializeToXml(
        xwriter,
        v => v.ID, // let's use ID as the vertex ID
        AlgorithmExtensions.GetEdgeIdentity(graph), // let QuickGraph give an id to edges
        "graph", "myvertex", "myedge", "" // names of the graph, vertex, node xml tags and the namespace uri
        );
}}
#### Deserializing graphs

To deserialize a graph, create the graph instance and call the {{DeserializeFromXml}}.

##### Serializing Custom Fields

The serializer supports the delegates to write additional information of the vertex, edge and graph types.