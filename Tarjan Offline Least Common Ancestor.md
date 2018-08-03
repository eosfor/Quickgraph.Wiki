### Tarjan Offline Least Common Ancestor

The [Tarjan off-line least common ancestor](http___en.wikipedia.org_wiki_Tarjan%27s_off-line_least_common_ancestors_algorithm) is an algorithm for computing lowest common ancestors for pairs of nodes in a tree (based on the union-find data structure). 

The {{AlgorithmExtensions.OfflineLeastCommonAncestorTarjan}} returns a delegate that can be queried for each pair. The delegate returns true if there is a common ancestor and assigns the out parameter.
{{
var g = new AdjacencyGraph<int, SEdge<int>>();
int root = ...; // root vertex
VertexPair<int> pairs = ...; // vertex pairs
var lca = g.OfflineLeastCommonAncestorTarjan(root, pairs);

// fetching the ancestor
TVertex ancestor;
foreach(var pair in pairs)
    if (lca(pair, out ancestor))
        Console.WriteLine("the ancestor of {0} is {1}", ancestor, pair); 
}}
