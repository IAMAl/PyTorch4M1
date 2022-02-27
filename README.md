# PyTorch Build for Apple Silicon
**NOTE**: This document is useful only for **scratch build** from source code for Apple Silicon.

## Work-flow
- install prerequisites
- download pytorch source from repository
- install pytorch through a wheel-build

## Test Environment
- Python 3.9.8
- macOS Montorey (ver.12.0.1)
- PyTorch 1.12 (2022/02/23@JST)
## Prerequisite Installation

### - CMake
**NOTE**: Compilation needs version 3.13 or greater of cmake.
```
$brew install cmake
```
### - OpenBLAS
```
$brew install openblas
```
### - Yaml
```
$python3 -m pip install pyyaml
```

## Download Source-code of PyTorch
```
git clone --recursive https://github.com/pytorch/pytorch
```

Enter to the directory;
```
$cd pytorch
```

## Setting CMakeList.txt
At line 184,
Apple Silicon does not support NVIDIA's CUDA;
```
option(USE_CUDA "Use CUDA" OFF)
```

At line 193,
Applie Silicon does not support AMD's ROCm;
```
option(USE_ROCM "Use ROCm" OFF)
```

At line 230,
Apple Silicon does not supprt NVIDIA's NCCL Library;
```
    USE_NCCL "Use NCCL" OFF
```
At line 232,
Apple Silicon does not supprt AMD's RCCL Library;
```
cmake_dependent_option(USE_RCCL "Use RCCL" OFF
```

At line 243,
Apple Silicon does not supprt NUMA Memory;
```
    USE_NUMA "Use NUMA. Only available on Linux." OFF
```


At line 252,
Apple Silicon does not supprt OpenMP;
```
option(USE_OPENMP "Use OpenMP for parallel code" OFF)
```
## Build
### - Compile Sorce-Code
Compile with berrow command;
```
$python3 setup.py build
```
### - Build Wheel
```
$python3 setup.py bdist bdist_wheel
```
## install
Wheel file is in "dist" directory.
You can use **pip install** for the wheel file.