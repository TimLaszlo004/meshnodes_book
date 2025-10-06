# Key principles

## Data-driven approach
The implementation follows data-driven approaches, which makes it easy to add new nodes in the future. This also means less boilerplate and less files with small graph file sizes - not that few kilobytes would hurt anyone.


## Explicit type system
It is not a secret, Blender's geometry nodes were the main inspiration. What seems sometimes cool in Blender, is the nodes accept different types of inputs and have different behavior with different types. But this also confuses some users, and it is harder to understand what a node actually does. In MeshNodes, no implicit conversions are allowed. All nodes have exactly one behavior and exactly one type of input set.

This decision might seem restrictive and might lead to more nodes, just for type conversions, but it ensures the clarity what should be expected from a node, and provides excellent options to debug: if a graph has produced an output from some input parameters, it should also work on other valid inputs. (Except of course geometry, math or Unity limitations (division by zero, reaching maximum vertex count in a mesh etc.))

## Render tree
Another big difference from other node based systems is the Output node. The Output node doesn't do anything, doesn't produce any output or consume any input, and anything can be connected to it.

Why is it useful? Some nodes already made the changes you wanted to make (like create and set the mesh of a GameObject), so the desired output is already there. **It just marks the nodes to be calculated.** In the background each node which is connected to the Output node will be calculated, which also results all the nodes to be calculated which are the dependencies of the selected nodes. So if you do not have unused nodes and connect each node to the outout node, you will get the same results (since all the nodes has to be calculated), but this is not recommended and sub-optimal.
Not connecting some nodes to the Output node is useful for drafts and debugging, when we do not want those nodes to be calculated.
