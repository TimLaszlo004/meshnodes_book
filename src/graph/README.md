## Editor features

MeshNodes consist of several components:
 - Editor code for displaying and editing the graph (Editor only, the build will not contain any of this)
 - Node data, used for the editor and runtime, actually a bunch of functions and data from the nodes (ports, variables, etc.)
 - Renderer: this is the NodeRenderer monobehaviour you can attach to any GameObject. This will execute the graph's logic. Currently this is the only renderer, although this incorporates mutliple features

 To know more about these features and learning how to use this system, read through this chapter carefully.
