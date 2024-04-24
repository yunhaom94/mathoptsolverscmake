# MathOptSolversCMake

CMake wrappers for mathematical optimization solvers.

For [Artelys Knitro](https://www.artelys.com/solvers/knitro/) see [fontanf/knitrocpp](https://github.com/fontanf/knitrocpp).

Example usage:
```cmake
# Fetch fontanf/mathoptsolverscmake.
set(MATHOPTSOLVERSCMAKE_USE_CLP ON)
FetchContent_Declare(
    mathoptsolverscmake
    GIT_REPOSITORY https://github.com/fontanf/mathoptsolverscmake.git
    GIT_TAG ...)
    #SOURCE_DIR "${PROJECT_SOURCE_DIR}/../mathoptsolverscmake/")
FetchContent_MakeAvailable(mathoptsolverscmake)

...

target_link_libraries(MyProject_my_target PUBLIC
    MathOptSolversCMake::clp)
```

## [CLP](https://github.com/coin-or/Clp)

* CLP will automatically be downloaded. It doesn't need to be already installed.
* Example:
```cmake
set(MATHOPTSOLVERSCMAKE_USE_CLP ON)

...

target_link_libraries(MyProject_my_target_1 PUBLIC
    MathOptSolversCMake::clp)
```

## [CBC](https://github.com/coin-or/Cbc)

* CBC will automatically be downloaded. It doesn't need to be already installed.
* Example:
```cmake
set(MATHOPTSOLVERSCMAKE_USE_CBC ON)

...

target_link_libraries(MyProject_my_target_2 PUBLIC
    MathOptSolversCMake::cbc)
```

## [FICO Xpress](https://www.fico.com/en/products/fico-xpress-optimization)

* FICO Xpress must be installed and a `XPRESSDIR` environment variable must be properly defined
* Currently only working on Linux, contributions welcome for Windows and macOS
* Example:
```cmake
set(MATHOPTSOLVERSCMAKE_USE_XPRESS ON)

...

target_link_libraries(MyProject_my_target PUBLIC
    MathOptSolversCMake::xpress)
```

## [IBM® ILOG CPLEX Optimizer](https://www.ibm.com/products/ilog-cplex-optimization-studio/cplex-optimizer)

* IBM® ILOG CPLEX Optimizer must be installed and a `CPLEX_HOME` environment variable must be properly defined (example: `/opt/ibm/ILOG/CPLEX_Studio129/`)
* Currently only working on Linux, contributions welcome for Windows and macOS
* Example:
```cmake
set(MATHOPTSOLVERSCMAKE_USE_CPLEX ON)

...

target_link_libraries(MyProject_my_target_1 PUBLIC
    MathOptSolversCMake::cplex)
target_link_libraries(MyProject_my_target_2 PUBLIC
    MathOptSolversCMake::cpoptimizer)
```

## [Gurobi](https://www.gurobi.com/)

* Gurobi must be installed and a `GUROBI_HOME` environment variable must be properly defined (example: `/opt/gurobi1003/linux64`)
* The Gurobi C++ interface must have been installed. For example, on Linux:
```
cd ${GUROBI_HOME}/linux64/src/build/
make
cp libgurobi_c++.a ../../lib/
```
* Currently only working on Linux, contributions welcome for Windows and macOS
* Example:
```cmake
set(MATHOPTSOLVERSCMAKE_USE_GUROBI ON)

...

target_link_libraries(MyProject_my_target PUBLIC
    MathOptSolversCMake::gurobi)
```
