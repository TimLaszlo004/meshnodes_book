# Rendering

Rendering is a term used for the process of actually executing the graph's logic. It involves traversing the graph's nodes and edges, and when the dependency tree is built, then it can execute it.

## Building the Dependency Tree
For knowing the dependencies of each node, we need to build a dependency tree. Starting with the Output node, each node will be visited and analyzed, till all nodes are visited, and hopefully all dependencies are known. This makes a tree-like structure (with a twist: see cache system), which will be used as an order to execute the nodes.

## Using the Dependency Tree
Once the dependency tree is built, we only need to traverse (depth-first search) and execute the nodes, if there are no nodes it depends on. Usually, the tree will end in the Input node, where the variables are set. After the tree was built there is no need to rebuild it, if the graph hasn't changed, the tree will be reused, and only the recalculating has to be redone.

## Cache system
One of the main usecases includes the case, where we want to update something in an Update loop. First thing: this is never a good idea, everything has its place and it is usually outside of the Update loop, I advise to use coroutine-based systems instead.
But for enabling this, and ensure fast recalculation, two cache system was used:
 - the first: once a graph is calculated, the result (output) will be stored. This way we do not calculate nodes more times than once in a single execution.
 - the second: if we already run the graph once, we only need to recalculate the nodes that have changed. In this case, the only node that can change, is the Input node, which is a reference to the graph's input data. The Input node's values will be compared with a cached input and only recalculate the subtree, which was impacted by the change. Note: the change in complex types (Transform, GameObject) is only checked as the Vector3's of the Transform (no component changes, no childcount changes)
