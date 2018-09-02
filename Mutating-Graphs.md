### Mutating Graphs

Most data structures are mutable and support batched addition/removal of vertices/edges.

#### Removing vertices with a predicate
```
var g = new AjacencyGraph<string, Edge<string>>();
...
// remove any vertex starting with foo
int removed = g.RemoveVertexIf(v => v.StartsWith("foo"));
Console.WriteLine("{0} vertices removed", removed);
```
