Advanced settings
===================================

Pin Groups
*********

Use Proximity Data
-------



Normalization
-------

The normalization options are used to normalize the pin group weights. Most of the time, tweaking this setting might be the key to achieve good pin groups and therefore nice results.

The normalization functions, and effects of different normalization functions on a simple example, are the following. All of the following examples weights are computed with *Use Proximity Data* enabled with default factor.

#. None normalization

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

#. Sigmoid normalization

    :math:`Norm(w = \text{weights}) =\frac{1}{1 + \exp[-f*(w-s)]}`

    .. image:: images/weights_normalization/sigmoid.png
       :width: 300

#. Tanh normalization (gain 0.8 and min 0.2)
    
    :math:`Norm(w = \text{weights}) =\tanh(g*w) + m`
    
    .. image:: images/weights_normalization/tanh_gain08_min02.png
       :width: 300

#. Arcsch normalization (gain 1. and min 0.)
    
    :math:`Norm(w = \text{weights}) = 1 - np.tanh(w/g) + m`
    
    .. image:: images/weights_normalization/arcsch_gain01_min0.png
       :width: 300

.. note::
    Mathematically, we are normalizing the cage pin group generated from the inverted bone group of the parent mesh, using the selected normalization function. We do this using the normalization function as value of the weight instead of the value of the weight itself.
    
    For those interested, you can plot these functions with `Desmos <https://www.desmos.com>`_.
