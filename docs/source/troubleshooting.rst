Troubleshooting
===================================

Errors
------

* **Error**: *An error occurred while remeshing. Try to re-restart Blender and re-try.*
  
  This error appears because of Blender remesher. We are working on a solution, for the moment the workaround if this happens is to save the file, close Blender and re-try.
  
* **Error**: *An error occurred while binding the mesh. Try with different Coverage and Resolution settings, or change Close Cage Method.*

  This error occurs because Blender can not bind the generated cage with the mesh. Try the following:
  * Decrease *Coverage* by steps of 0.05
  * Increase/decrease *Remesh* *Resolution* by steps of around 100/300
  * Change *Close Cage method*
  * Change *Deform method* to *Mesh Deform*. Use this only as last resource, as this method has some limitations, see :ref:`Deform Method<Deform Method>`.

Physics Simulation
------

* Cages are not simulating physics correctly.
  
  Sometime Blender caches the physics and does not flush them when a new simulation is started. To solve most of the issues, you should go in the Physics Cloth settings of the cage and manually change the final frame value on the Cache tab. This will force Blender to consider the current cache obsolete.
