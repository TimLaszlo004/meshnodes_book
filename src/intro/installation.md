# Installation

The installation steps are as follows:
 - go to Unity Assetstore
 - buy the MeshNodes package
 - import the package into your Unity project via the Unity Package Manager

## Good to know:
 - OS independent, works directly with the Unity Mesh API
 - Should work fine with latest Unity versions (only tested on Unity 6)
 - You may encounter issues, but every error you encounter is either based on the Unity Editor elements, which does not influence the runtime behaviour or it will print a (hopefully helpful) message indicating the issue
 - You can make unused 3D meshes, which will pollute memory. This is because Unity's Asset Management. Be sure to use it wisely and/or delete the unused meshes if the your project needs temporary meshes, which are not used later
