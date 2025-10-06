# Known issues

There are a few issues I have encountered while working with this project:
 - the serialization is not always correct: if you close a project and then reopen it, you might find the window restored, but it might not know the underlying asset anymore
    - the best workaround for this: if you try 'Show In Project' and then double click the asset, if it opens a new window, use the new window
 - It is more like a missing feature, but currently there is no easy support for deleting unused input variables, you can delete them manually in the assets inspector window in the InputPorts_ list, but this will mess up the edges, if you delete from the middle: the edges store the node's port id, which will be changed with this action. Support is planned in the future.
  - No support for graceful error handling: if you do not ensure enough data for each node to calculate with, then the renderer will throw errors. You should fix it either way, before you build, but it could be less scary.
