#### DataSetGraph

The `DataSetGraph` is a directed graph of a `DataSet` schema, where each table is a vertex and each table relation is an edge.

* Requires `QuickGraph.Data.dll` 

##### Creating the `DataSetGraph`

You can create the graph from any `DataSet` by using the `ToGraph` extension method.
```
using QuickGraph.Data; // extension methods
...

DataSet ds = ...;
var g = ds.ToGraph();
```

##### Topological Sort

A very useful application of the `DataSetGraph` is to compute the topological sort of the table. The topological sort gives you the order in which you should fill tables (or reversely delete them).

```
foreach(var table in g.TopologicalSort())
    ...
```