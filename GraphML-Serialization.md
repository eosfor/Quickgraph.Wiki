#### GraphML Serialization

[GraphML](http://graphml.graphdrawing.org/) is a comprehensive and easy-to-use file format for graphs. QuickGraph supports loading and saving directed graphs to this format. The GraphML serialization APIs are exposed through the `GraphMLExtensions` extension methods (in `QuickGraph.Serialization`).

The serialization code uses dynamic code generation to provide high performance in reading and writing custom properties.

##### Serializing graphs

To serialize a graph, simply call the `SerializeToGraphML` extension methods with an `XmlWriter` instance.
```
var g = new AdjacencyGraph<int, Edge<int>>();
...
using(var xwriter = XmlWriter.Create(...))
    g.SerializeToGraphML(xwriter);
```
#### Deserializing graphs

To deserialize a graph, create the graph instance and call the `DeserializeFromGraphML`:
```
var g = new AdjacencyGraph<int, Edge<int>>();
using(var xreader = XmlReader.Create(...))
     g.DeserializeFromGraphML(xreader, 
         id => int.Parse(id), 
         (source, target, id) => new Edge<int>(source, target)
     );
```

##### Serializing Custom Fields

The serializer supports the `XmlAttributeAttribute` attribute on public properties of the vertex, edge and graph types. These properties will be declared and serialized in the GraphML stream. The supported property types are `bool`, `int`, `long`, `float`, `double` and `string`. 

```
class IntEdge : Edge<int> {
   ...
   [XmlAttribute("name")](XmlAttribute(_name_))
   public string Name {get;set;}
}
```

Default values can also be specified for the properties by using the {{DefaultValueAttribute}} attribute:
```
   ...
   [XmlAttribute("name")](XmlAttribute(_name_))
   [DefaultValue("unknown")](DefaultValue(_unknown_))
   public string Name {get;set;}
```
