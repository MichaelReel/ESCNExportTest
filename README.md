# ESCNExportTest
Testing the .escn exporter in blender, trying various capabilities

## Blender Process

  1. Install [ESCN Exporter](https://github.com/godotengine/godot-blender-exporter).
     - Should only need to do this once
  
### Creating a mesh

  1. Create a new general scene.
  1. Hide or delete the camera and the light.
  1. Edit the cube mesh, or delete it and create a new mesh (or meshes).
 
### Create a new texture for a mesh

  1. While in `Edit Mode` mark any obvious seam edges by selecting them and using the right click menu -> `Mark Seam`.
  1. On the top tab bar select `UV Editing`. This should open the UV Editing window on the left.
  1. The `Edit Mode` window should still be open on the right. In this window select all the vertices.
  1. From the `Edit Mode`, click the `UV` menu and select "Unwrap".
  1. From the `UV Editing` window, modify the UV map to preferred layout.
  1. From the `UV Editing` window, click the `UV` menu and select `Export UV Layout`. Export the layout image to the project directory.
  1. From the `UV Editing` window, click the `Image` menu and select `Open`. Select the UV layout file that was just saved.
     - This should show an image that lines up with the UV layout, it might be difficult to see without zooming in to check.
  1. Change the `Edit Mode` window the the `Object Mode`, the mesh should still be selected.
  1. On the object `Properties` panel (might need to enable this view) open the `Material Properties` tab.
  1. If there is no material on this mesh, then click the `+` `New` button.
  1. Click the button to the right of the `Base Color` field, and select the `Image Texture` option from the `Texture` column.
  1. An `Open` button should have appeared, click this and select the UV layout image created earlier.
  1. Change the `Object Mode` window to `Texture Paint`, this should show the edges in black on the mesh from the UV layout image.
  1. From the `Texture Paint` window, drawing on the mesh should show changes on the `UV Editing` window.
  1. Draw whatever is required to texture the mesh and then change the `Texture Paint` window back to the `Object Mode`.
  1. From the `UV Editing` window, select `Image*` -> `Save` to keep changes to the UV layout texture.

### Creating an armature/bones/skeleton

  1. A good place to start is to put the origin of the mesh at the pivot point between the feet for positioning on terrain so animations have a contact position.
  1. If finished with the UV/Texture editing, click the `Layout` tab on the main tab bar for more effective use of screen space.
  1. In `Object Mode`, select from the menu `Add` -> `Armature`
  1. With the armature created it should probably also be renamed.
     - Bones can be renamed on the `Outliner` panel.
  1. In `Edit Mode` and with the first bone of the armature selected, `Shift` + `E` will add a new bone attached to the last.
  1. Draw all the bones in relation to the structure of the model
  1. In the `Object Mode` select the mesh, and holding shift, select the Armature. With both selected click `Ctrl` + `P` to get the parenting menu, then use one of the parenting options to create the vertex groups. The armature becomes the parent object.
     - The vertex groups will be created and visible under the mesh in the `Outliner` panel.
     - If creating empty vertex groups there won't be any auto-linking, vertex groups will need to be populated with vertices manually. In edit mode, select some vertices then click `Ctrl` + `G` to get the vertex grouping menu.
     - If using the auto-linking functions, the results can be observed in `Edit Mode` with the `Object Data Properties` panel open. Each vertex group can be highlighted and the `Select` and `Deselect` buttons can be used to show how the groups have been composed.
     - Vertices can be added to, or removed from, the *currently active vertex group*. Groups are activated by selecting them from the vertex group menu, or from the `Object Data Properties` panel.

### Creating poses/animations

  
### Export the scene for use in Godot

  1. From the main menu, select `File` -> `Export` -> `Godot Engine (.escn)` and save the scene to the project directory.

## From Godot

  1. If the .escn file has been saved to the Godot project directory, it should be possible to double click it in the FileSystem view and be given the option to `Open Anyway` in read only mode, or `New Inherited` to create a copy that can be saved as an editable scene.

