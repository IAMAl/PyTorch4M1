# PyTorch Build for Apple Silicon

## Test Environment
- Python 3.8.2 (Pre-installed)
- macOS Big Sur (ver.11.1)

## Prerequisite Installation

### homebrew
https://zenn.dev/ress/articles/069baf1c305523dfca3d

### OpenBLAS for Apple Silicon
$=brew install openblas

### Download Source-code of PyTorch
$git clone --recursive https://github.com/pytorch/pytorch
$cd pytorch

### Paste three files to the pytoch directory
**NOTE** OpenCV will be not installed, if you want it then you need to set "OK" in the cmake file.

### Build
$/usr/bin/python3 setup.py build

### Install
$sudo /usr/bin/python3 setup.py develop && /usr/bin/python3 -c "import torch"
