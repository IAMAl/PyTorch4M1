# PyTorch Build for Apple Silicon
**NOTE**: This document is useful only for **scratch build** from source code for Apple Silicon.

## Work-flow
- install prerequisites
- download PyTorch source from repository
- install PyTorch through a wheel-build, or standard install

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

## Download the source-code of PyTorch
```
git clone --recursive https://github.com/pytorch/pytorch
```

Enter the directory;
```
$cd pytorch
```

## Setting CMakeList.txt
pThead is not supported on OS-X;
```
set(THREADS_PREFER_PTHREAD_FLAG OFF)
```

OS-X does not support Microsoft VisualStudio, so comment-out between these lines;
```
if(MSVC)
```
and
```
endif(MSVC)
```

And, setting APPLE as **TRUE**.

At line 184,
Apple Silicon does not support NVIDIA's CUDA;
```
option(USE_CUDA "Use CUDA" OFF)
```
Apple Silicon does not support NVIDIA's cuDNN;
```
USE_CUDNN "Use cuDNN" OFF
```

At line 193,
Apple Silicon does not support AMD's ROCm;
```
option(USE_ROCM "Use ROCm" OFF)
```

At line 230,
Apple Silicon does not support NVIDIA's NCCL Library;
```
    USE_NCCL "Use NCCL" OFF
```
At line 232,
Apple Silicon does not support AMD's RCCL Library;
```
cmake_dependent_option(USE_RCCL "Use RCCL" OFF
```

At line 243,
Apple Silicon does not support NUMA Memory;
```
    USE_NUMA "Use NUMA. Only available on Linux." OFF
```


At line 252,
Apple Silicon does not support OpenMP;
```
option(USE_OPENMP "Use OpenMP for parallel code" OFF)
```
## Build for Wheel-based Install
### - Compile Sorce-Code
Compile with below command;
```
$python3 setup.py build
```
### - Build Wheel
```
$python3 setup.py bdist bdist_wheel
```
### - Install
Wheel file is in "dist" directory.
You can use **pip install** for the wheel file.

## Build for Standard-Install
### - Compile Sorce-Code
Compile with below command;
```
$python3 setup.py build
```
### - Install
```
python3 setup.py develop && python3 -c "import torch"
```