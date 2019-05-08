# Calculation of Euclidean distances between periodic images

## Description
Python code to calculate euclidean distances between periodic images in a (molecular dynamics)
simulation trajectory. Returns the minimum distance between periodic images, which is useful to
determine if the simulation box is too small and the periodic images 'see' each other. Functionality
equivalent to `g_mindist` of the GROMACS suite ([url](http://manual.gromacs.org/documentation/2018/onlinehelp/gmx-mindist.html)).

## Requirements

* Python libraries:
    - cython
    - numpy
    - mdtraj
    - OpenMM (for mmCIF support)

* Other:
    - OpenMP (for parallelizable version)

## Installation
```
git clone https://github.com/JoaoRodrigues/pbc_mindist
cd pbc_mindist
python setup.py build_ext --inplace
python mindist.py yourtrajectory.dcd yourtopology.pdb --backbone
```

## Caveats
- OOB support for protein trajectories only (selections all do `protein and ...`)
- Reimaging function will fail with `--alpha_carbons`. Reimage trajectory first
and save the coordinates/topology separately. 
- Not tested on Windows/OSX
- Compilation will fail without OpenMP (setup.py could use fixing...)