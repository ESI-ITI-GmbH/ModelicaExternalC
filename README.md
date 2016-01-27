# ModelicaExternalC
SimulationX specific ModelicaExternalC.lib to link external C/C++ code with

## Description
### Simulation with internal solvers (ME)BDF
Simulation with internal solvers (ME)BDF requires the external code to be available as an executable binary (DLL). Therefore (with MSVC compilers) compile and link the external DLL against ModelicaExternalC.lib that also is part of the installation of SimulationX. The /MD switch can be used for compilation but is not necessary.

### Simulation with external solvers (CVODE, Fixed-Step-Size solvers)
* DLL is supported as with (ME)BDF.
* There is an additional compile/link step and thus the external code can be compiled or a precompiled static library (LIB) can be linked. The /MD switch shall be used for compilation of the LIB.

### Code-Export Executable Model
* For sake of portability the safest thing is to completely stay on source level.
* It is also possible to link against a precompiled static library but it requires that the run-time library setting (i.e. /MD or /MT) of LIB and executable binary match. By default it is /MT. This LIB can also be used with Dymola.
* It is also possible to dynamically load a DLL but then there is the question where the ModelicaUtilities functions come from. It is not recommended to use the DLL compiled for (ME)BDF.

## Summary
* DLL (linked against ModelicaExternalC.lib) with /MD for built-in simulation
* LIB (with unresolved ModelicaUtilities) with /MT for stand-alone executable model on Windows platform
* C/C++ code for stand-alone executable model on any other platform
