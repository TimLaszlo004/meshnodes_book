# Develop

## How to make new node
Easy - open Nodes.cs, add a new element to the NodeType enum (if you add it in the middle you will break existing graphs). Then add a new entry to the GetNodeInformations function. Here you can define the properties of the new node. You also have to assign a function for the node in the GetNodeInformations function, you are free to write the function at the end of the file.

If you make a node which makes a new object of some kind, take a look at the existing cache nodes, and use the same cache system. This will save this new object in the graph, so if it is rerun, it will reuse the same object to avoid creating new objects (textures, meshes, game objects).

## How to make a new port type
Making a new port type is a bit more complicated. You first have to add a new element to the PortType enum in Nodes.cs, and add the name to PortTypeToString function. This will allow you to use the new port inside the graph. For using it as an input, you have to add and handle this new port type in the InputVariable class and in NodeRendererEditor.cs. After this it should be working fine.
