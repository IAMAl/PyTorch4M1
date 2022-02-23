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