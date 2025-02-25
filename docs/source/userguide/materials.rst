=========
Materials
=========

Materials are key components of hydrogen transport simulations. They hold the properties like diffusivity, solubility and even thermal properties like thermal conductivity or heat capacity.

To define a material, use the :code:`Material` class:

.. code-block:: python

    mat1 = Material(id=1, D_0=2, E_D=0.1)
    mat2 = Material(id=2, D_0=3, E_D=0.4)


Materials are then assigned to the model:

.. code-block:: python

    my_model = Simulation(materials=[mat1, mat2])

----------------------
Parameters description
----------------------

The :code:`Material` class has three required arguments:

* :code:`id`: a unique id given to the material/volume. It is useful when defining volumetric source terms or exports. Several ids can be given to the same material if multiple volumes have the same material.
* :code:`D_0`: the diffusivity pre-exponential factor expressed in m2/s
* :code:`E_D`: the diffusivity activation energy in eV

Some other parameters are optional and are only required for some types of simulations:

* :code:`S_0`: the solubility pre-exponential factor, its units depend on the solubility law (Sievert's or Henry)
* :code:`E_S`: the solubility activation energy in eV
* :code:`thermal_cond`: the thermal conductivity in W/m/K
* :code:`heat_capacity`: the heat capacity in J/kg/K
* :code:`rho`: the volumetric density in kg/m3


--------------------
Integration with HTM
--------------------

H-transport-materials (HTM) is a python database of hydrogen transport properties.
Using this database will avoid making copy-pasting errors and add consistency across simulations by making sure the same properties are used.
HTM can be easily `integrated with FESTIM <https://github.com/RemDelaporteMathurin/FESTIM-workshop/blob/main/tasks/task8.ipynb>`_.
