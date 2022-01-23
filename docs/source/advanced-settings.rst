Advanced settings
===================================

Pin Groups
*********

Normalization
-------

The normalization options are used to normalize the pin group weights. Most of the time, tweaking this setting might be the key to achieve good results.

The effect of different normalization functions on a simple example is the following.

#. None normalization

    .. image:: images/weights_normalization/none.png
       :width: 300

#. Linear normalization

    .. image:: images/weights_normalization/linear.png
       :width: 300

#. Square normalization

    .. image:: images/weights_normalization/square.png
       :width: 300

#. Sigmoid normalization

    .. image:: images/weights_normalization/sigmoid.png
       :width: 300

#. Tanh normalization (gain 0.8 and min 0.2)

    .. image:: images/weights_normalization/tanh_gain08_min02.png
       :width: 300

.. note::
    Mathematically, we are normalizing the cage pin group generated from the inverted bone group of the parent mesh, using the selected normalization function.
    
    For those interested, you can plot these functions with `Desmos <https://www.desmos.com>`_.
