## Comments
//Nanta

1) Source these module on Athena before compiling zstruct

`$ module load openmpi/3.1.2-intel_oneapi`

`module load intel/oneapi/mkl/2021.1.1`

`module load gcc/12.1.0`

Then compilation with `pixi run start` (see below)

2) This code is compiled with the following option: SKIPDFT 1
3) Modification done in this fork.
   - unactivate remnant of code sections that submit DFT job (./qmakegf)

## ZStruct
code for ZStruct-2

## Overview

ZStruct is a package for automated reaction discovery developed in C++.

For more information, check out the wiki page (somewhat out of date but hopefully still useful): https://github.com/ZimmermanGroup/ZStruct/wiki

Sample tutorial files can be found under the tutorial folder: https://github.com/ZimmermanGroup/ZStruct/tree/master/tutorial

## Installation

First, clone this github repository.

Aug 2024: Attempting a more reproducible build with [Pixi](https://pixi.sh), a tool built on the conda ecosystem to manage both dependencies and configuration / installation workflows.

The pixi.toml file in this repository specifies the dependency package names as they appear on [conda-forge](https://conda-forge.org/) and installation tasks. You can use pixi (simple installation instructions [here](https://pixi.sh)) to install the dependencies and execute the build, or reference the pixi.toml and do something equivalent using your preferred tools.

With pixi, I built ZStruct by navigating into the ZStruct git repository and executing `pixi run start` which installs the dependencies, executes the Makefile, and if successful runs the built executable.

Notes: The build has succeeded in a github actions environment which is a freshly cloned linux virtual machine. On our computing cluster, I find that I either need to unload one of our default linux modules or clear the LD_LIBRARY_PATH with `export LD_LIBRARY_PATH=""`. I assume this avoids a conflicting version of some dependency taking priority over the version installed for ZStruct.
