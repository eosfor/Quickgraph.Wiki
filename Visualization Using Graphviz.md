#### Visualization Using Graphviz

QuickGraph supports generating _dot files_, the file format of [Graphviz](Graphviz). All Graphviz related code are located in the {{QuickGraph.Graphviz.dll}} assembly.

##### Basic graph rendering

The {{GraphvizAlgorithm}} class contains the logic to render a {{IVertexAndEdgeListGraph}}. 
* {{GraphFormat}}, {{CommonVertexFormat}} and {{CommonEdgeFormat}} control the default 'looks' of the generated graph,
* {{FormatVertex}} and {{FormatEdge}} events let you customize the display of individual vertices and edges.

{{
IVertexAndEdgeListGraph<TVertex,TEdge> g= ...;
var graphviz = new GraphvizAlgorithm<TVertex,TEdge>(g);

// render
string output = graphviz.Generate(new FileDotEngine(), "graph");
}}

##### Custom Rendering of Dot

QuickGraph sends the generated {{dot}} code to a 'dot engine' interface which is supposed to do the rest of the work. This is where you can plugin and add any additional steps. QuickGraph provides a simple rendering engine that writes the dot file to disk :)

{{
public interface IDotEngine
{
    // renders the dot code and returns the name of the generated file
    string Run(
        GraphvizImageType imageType,
        string dot,
        string outputFileName);
}
}}