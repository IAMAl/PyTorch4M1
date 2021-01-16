# PyTorch Build for Apple Silicon

## Test Environment
- Python 3.8.2 (Pre-installed)
- venv
- macOS Big Sur (ver.11.1)

## Prerequisite Installation

### homebrew
https://zenn.dev/ress/articles/069baf1c305523dfca3d

### OpenBLAS for Apple Silicon
This is based on above setting.
Currently OpenBLAS supports M1.

$=brew install openblas

### Download Source-code of PyTorch
git clone --recursive https://github.com/pytorch/pytorch

Enter to the directory;

$cd pytorch

### Paste three files to the pytoch directory
**NOTE** if you want OpenCV setting then you need to set "OK" in the cmake file.

### Build
$python3 setup.py build

### Build Wheel
$python3 setup.py bdist bdist_wheel

### install
You can use **pip install** for the wheel file.