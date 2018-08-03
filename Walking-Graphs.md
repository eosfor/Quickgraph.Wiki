#### Walking Graphs

##### Iterate vertices
Use the {{Vertices}} property to get an enumerable collection of vertices:
{{
foreach(var v in g.Vertices)
    Console.WriteLine(v);
}}
##### Iterate edges
Use the {{Edges}} property get an enumerable collection of edges:
{{
foreach(var e in g.Edges)
    Console.WriteLine(e);
}}
##### Iterate out edges
The {{OutEdges}} method returns an enumerable collection of out-edges:
{{
foreach(var v in g.Vertices)
    foreach(var e in g.OutEdges(v))
        Console.WriteLine(e);
}}
Similarly, {{InEdges}} returns an enumerable collection of in-edges.
