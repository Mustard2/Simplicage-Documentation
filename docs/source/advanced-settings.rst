Advanced settings
===================================

Cage
*********

Covarage
-------

This option controls how much of the selected bone vertex group is considered when generating the cage.

In the example, the vertex group on the sphere of the selected bone has non-null values on the whole spehere. Therefore a coverage of 1 will create a cage covering the whole sphere. When selecting 0.5 instead, we cover half the sphere.

#. *Coverage* = 1

    .. image:: images/covarage_1.png
           :width: 300

#. *Coverage* = 0.5
    
    .. image:: images/covarage_05.png
           :width: 300

Re-size Scale
-------

*Re-size Scale* is the factor with which the final cage is rescaled using the cage *Origin to Center of Mass (Surface)* point as the origin.

.. info::
    We advise to use a value slightly bigger than 1 for physics cages, and a value of 1 for Colllision cages.

#. *Re-size Scale* = 1

    .. image:: images/scale_1.png
           :width: 300

#. *Re-size Scale* = 1.05
    
    .. image:: images/scale_105.png
           :width: 300

.. warn::
    If the mesh is complex, the rescaling might be not perfect due to the choice of the origin. While this is not an issue when using Surface Deform binding option (see below), it might be a problem when using Mehs Deform as the cage might fail to enclose the whole mesh. In this case, small manual tweaks of the mesh might be needed.

Pin Groups
*********

Pin vettex groups define which parts of the cage will be affected by the cloth simulation, and therefore which parts will actually be moved. In the vertex groups, each vertex has a weight assigned. In the case of pin groups, when the weight is 1, the simulation will not act on that vertex; on the contrary, a null value means that the vertices will fully partecipate in the simulation. In between values can be useful to smooth out the transition between pinned part (weight = 1) and simulated parts (weight = 0).

In the images below, 0 values are depiced with blue color, and 1 values are depincted with red. Green/yellow color depicts in between values.

Use Proximity Data
-------

With *Use Proximity Data*, the cage pin group will be generated setting weights to 0 for all vertices that are near the cage mesh. Higher values of the factor can be used to increase the distance.

#. *Use Proximity Data* disabled

    .. image:: images/no_use_proximity.png
           :width: 300

#. *Use Proximity Data* enabled with default factor 0.02

    .. image:: images/use_proximity_002.png
           :width: 300

#. *Use Proximity Data* enabled with max factor 0.2

    .. image:: images/use_proximity_02.png
           :width: 300

Normalization
-------

The normalization options are used to normalize the pin group weights. Most of the time, tweaking this setting might be the key to achieve good pin groups and therefore nice results.

The normalization functions, and effects of different normalization functions on a simple example, are the following. All of the following examples weights are computed with *Use Proximity Data* enabled with default factor.

#. None normalization

    :math:`Norm(w = \text{weights}) = 0`

    This function effectively set all weights to 0. If *Use Proximity Data* is disabled, the pin group would be all null. If enabled like in the figure, you still get a nice pinning on the part flat part of the half sphere.
    
    It is useful to create simple weights, or without *Use Proximity Data* when we want to create a cage that is not pinned. In the latter case, the whole mesh will be simulated and it will interact with collision objects.

    .. image:: images/weights_normalization/none.png
       :width: 300

#. Linear normalization
    
    :math:`Norm(w = \text{weights}) = w`
    
    .. image:: images/weights_normalization/linear.png
       :width: 300

#. Square normalization

    :math:`Norm(w = \text{weights}) = w^2`

    .. image:: images/weights_normalization/square.png
       :width: 300

#. Sigmoid normalization (default values)

    :math:`Norm(w = \text{weights}) =\frac{1}{1 + \exp[-f*(w-s)]}`

    .. image:: images/weights_normalization/sigmoid.png
       :width: 300

#. Tanh normalization (gain 0.8 and min 0.2)
    
    :math:`Norm(w = \text{weights}) =\tanh(g*w) + m`
    
    .. image:: images/weights_normalization/tanh_gain08_min02.png
       :width: 300

#. Arcsch normalization (gain 1. and min 0.)
    
    :math:`Norm(w = \text{weights}) = 1 - \tanh(w/g) + m`
    
    .. image:: images/weights_normalization/arcsch_gain01_min0.png
       :width: 300

.. note::
    Mathematically, we are normalizing the cage pin group generated from the inverted bone group of the parent mesh, using the selected normalization function. We do this using the normalization function as value of the weight instead of the value of the weight itself.
    
    For those interested, you can plot these functions with `Desmos <https://www.desmos.com>`_.
