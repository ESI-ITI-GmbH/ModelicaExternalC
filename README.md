# ModelicaExternalC
SimulationX specific ModelicaExternalC.lib to link your external C/C++ code with

## Description
### Simulation with BDF or MEBDF method
The Simulation with the BDF method or MEBDF requires the external code to be available as an executable binary (DLL). Therefore (with MSVC compilers) compile and link the external DLL against ModelicaExternalC.lib that also is part of the installation of SimulationX. The /MD switch can be used for the compilation of your external library, but is not necessary.

### Simulation with CVODE method, Fixed Step Size solver, BDF (Compiled Code) or MEBDF (Compiled Code)
* DLL is supported as with the BDF method or MEBDF method.
* There is an additional compile/link step and thus your external code can be compiled or a precompiled static library (LIB) can be linked. The /MD switch shall be used for the compilation of your external library LIB.

### Code-Export Executable Model
* If portability is an issue for you, it is recommended to completely stay on C/C++ source level.
* It is also possible to link against a precompiled static library but it requires that the run-time library setting (i.e. /MD or /MT) of your LIB and the executable binary match. By default it is /MT. Your LIB can also be used with Dymola.
* It is also possible to dynamically load a DLL, but the [question](https://trac.modelica.org/Modelica/ticket/2191) is where the ModelicaUtilities functions come from. It is not recommended to use the external DLL (with resolved ModelicaUtility symbols) that linked against this SimulationX specific ModelicaExternalC.lib.

## Summary
* DLL (linked against ModelicaExternalC.lib) with /MD for built-in simulation with all solver methods
* LIB (with unresolved ModelicaUtilities) with /MT for stand-alone executable model on Windows platform
* C/C++ code for stand-alone executable model on any other platform
