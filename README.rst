######################################################
composite uFJC scission Lake-Thomas fracture toughness
######################################################

A repository that incorporates the composite uFJC scission model within the Lake-Thomas theory of polymer fracture. This repository is dependent upon the `composite-uFJC-scission <https://pypi.org/project/composite-ufjc-scission/>`_ Python package.

*****
Setup
*****

Once the contents of the repository have been cloned or downloaded, the Python virtual environment associated with the project needs to be installed. The installation of this Python virtual environment and some essential packages is handled by the ``virtual-environment-install-master.sh`` Bash script. Before running the script, make sure to change the ``VENV_PATH`` parameter to comply with your personal filetree structure.

*****
Usage
*****

There are three Python codes in this repository: ``AFM_chain_tensile_test_curve_fit.py``, ``fracture_toughness.py``, and ``fracture_toughness_sweep.py``. Each of these codes creates an object that can perform a "characterization" routine, a "finalization" routine, or both routines (where the characterization routine must preceed the finalization routine). The characterization routine performs a variety of calculations, and saves the results of those calculations in pickle files or text files stored within appropriately named directories (``.\AFM_chain_tensile_test_curve_fit\``, ``.\fracture_toughness\``, and ``.\fracture_toughness_sweep\``). The finalization routine then loads the contents of those pickle files or text files, plots the results, and saves the plots back in the appropriate directory. Before running each Python code, make sure you confirm which routines you want to execute. As a means of precaution, the codes provided in this repository only have the finalization routine activated (with the characterization routine commented out, but this routine can be un-commented out if desired).

These Python codes are written in a parallelized computing fashion, *vis-à-vis* the ``mpi4py`` package. In order to run each code, first activate the Python virtual environment, and then execute the following command in the terminal:

::

    mpiexec -n number_of_cores python3 {AFM_chain_tensile_test_curve_fit, fracture_toughness, fracture_toughness_sweep}.py

You can modify the number of cores called upon by replacing ``number_of_cores`` with that number. In my experience, the runtime of the characterization routine seems to be optimized when calling upon 8 cores. On my computer running 8 cores, the characterization routine of the ``AFM_chain_tensile_test_curve_fit.py``, ``fracture_toughness.py``, and ``fracture_toughness_sweep.py`` codes takes roughly 1 minute, 1 hour, and 1.5-2 days to complete, respectively.

***********
Information
***********

- `Releases <https://github.com/jasonmulderrig/composite-uFJC-scission-lake-thomas-fracture-toughness/releases>`__
- `Repository <https://github.com/jasonmulderrig/composite-uFJC-scission-lake-thomas-fracture-toughness>`__

********
Citation
********

\Jason Mulderrig, Samuel Lamont, Franck Vernerey, and Nikolaos Bouklas, Accounting for chain statistics and loading rate sensitivity in the Lake-Thomas theory of polymer fracture, In preparation.

\Jason Mulderrig, Brandon Talamini, and Nikolaos Bouklas, ``composite-ufjc-scission``: the Python package for the composite uFJC model with scission, `Zenodo (2022) <https://doi.org/10.5281/zenodo.7335564>`_.

\Jason Mulderrig, Brandon Talamini, and Nikolaos Bouklas, A statistical mechanics framework for polymer chain scission, based on the concepts of distorted bond potential and asymptotic matching, `Journal of the Mechanics and Physics of Solids 174, 105244 (2023) <https://www.sciencedirect.com/science/article/pii/S0022509623000480>`_.
