# PyTorch Build for Apple Silicon
**NOTE**: PyTorch supports Apple Silicon now (you can install with pip)

This document is useful only for scratch build from source code for Apple Silicon.

## Work-flow
- install conda
- install prerequisites
- install pytorch through a wheel-build

## Install conda

```bash
$ cd ~/Downloads
$ wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh
$ chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
$ sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
$ source ~/miniforge3/bin/activate
```

## Install Python 3.8 with conda and activate virtual environment

```bash
$ conda create --name pytorch python=3.8
$ conda activate pytorch
```

## PyTorch Prerequisites

```bash
$ conda install astunparse ninja pyyaml cffi typing_extensions future requests dataclasses
```

**How to install miniforge** Outdated: homebrew supports Apple Silicon now

## Test Environment
- Python 3.8.2 (Pre-installed)
- venv
- macOS Big Sur (ver.11.1)

## Prerequisite Installation

### homebrew
**NOTE** Outdated: homebrew supports Apple Silicon now

https://zenn.dev/ress/articles/069baf1c305523dfca3d

### OpenBLAS for Apple Silicon
This is based on above setting.
Currently OpenBLAS supports M1.

```bash
$ brew install openblas
```

### Download Source-code of PyTorch
```bash
$ git clone --recursive https://github.com/pytorch/pytorch
```

Enter to the directory;

```bash
$ cd pytorch
```

### Paste three files to the pytoch directory
**NOTE** if you want OpenCV setting then you need to set "OK" in the cmake file.

### Build
```bash
$ python3 setup.py build
```

### Or build with OpenCV enabled
```bash
$ USE_OPENCV=1 python3 setup.py build
```

### Build Wheel
```bash
$ python3 setup.py bdist bdist_wheel
```

### BONUS: Install torchvision

```bash
$ conda install torchvision -c pytorch
```

### install
You can use **pip install** for the wheel file.
