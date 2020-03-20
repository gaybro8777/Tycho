# Tycho
[![Arxiv Citation](http://img.shields.io/badge/arXiv-2002.12375-green.svg?style=flat)](https://arxiv.org/abs/2002.12375)
[![TRAVIS Status](https://travis-ci.org/JPGlaser/Tycho.svg?branch=Py3_version)](https://travis-ci.org/github/JPGlaser/Tycho)

AMUSE (Astrophysical Multipurpose Software Environment) community code for observing star-star scattering effects on exoplanets in stellar clusters.

*TYCHO* is a simulation suite used in observing the effects of star-star scattering on exoplanets within clustered natal environments. It is dependent on multiple community codes provided by the Astrophysical Multipurpose Software Environment (AMUSE; amusecode.org).

## Developers' Note
We currently working on converting *TYCHO* to the latest version of Python3, which will support AMUSE 13.1 +. The Python2 version can be accessed in the version history and works well for AMUSE 11.

## Breakdown of Included Scripts
- **sim_cluster.py:** Used in simulating a star cluster according to user-defined initial conditions. Additionally, it records all stellar close-encounters into an easy to process pickle format. If desired, this can also include a Jovian population to track the sub-brown dwarf population in the cluster.
- **cut_encounters.py:** Used to place predefined data cuts on the close-encounter database generated by *sim_cluster.py*.
- **gen_RandEncounters.py:** Used to create the starting conditions for *sim_encounters.py* by generating random orientations of the desired planetary systems for each encounter specified in the reduced encounter database.
- **sim_encounters.py:** Used in simulating stellar close-encounters created and stored by *gen_RandEncounters.py*.
- **gen_init-final_database.py:** A useful script which generates the initial and final conditions of planetary systems after *sim_encounters.py* has been run.

===============================================================

## Installation on Ubuntu 18 LTS
Before you install Tycho, you need to install the following software prerequisites:
```
$ sudo apt-get install build-essential gfortran python3-dev \
  libopenmpi-dev openmpi-bin \
  libgsl-dev cmake libfftw3-3 libfftw3-dev \
  libgmp3-dev libmpfr6 libmpfr-dev \
  libhdf5-serial-dev hdf5-tools \
  git
```
Additionally, you will need an updated Python distribution, such as Anaconda3. This can be achieved by completing the following:
```
cd Downloads
wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
bash Anaconda3-2020.02-Linux-x86_64.sh
```
You'll want to initialize *conda* when prompted. After starting a new terminal session, run the following:
```
$ pip install numpy nose docutils mpi4py h5py wheel scipy astropy jupyter pandas seaborn rebound
$ pip install amuse-framework
$ pip install amuse-ph4 amuse-kepler amuse-sse amuse-seba amuse-smalln
```
Finally, switch to a directory that you'd like for Tycho to be installed into and run:
```
$ cd ABSOLUTE_PATH_TO_REPOSITORY/
$ git clone https://github.com/JPGlaser/Tycho.git
```
You'll need to add the *src* folder inside of the git repository to your $PYTHONPATH:
```
$ nano .profile
## Add the following to the end of the file:
## export PYTHONPATH="ABSOLUTE_PATH_TO_REPOSITORY/Tycho/src:$PYTHONPATH"
```

## Production Walk-Through
Before you begin using Tycho,
