# SplinePSF
This is a factored out implementation repository of the spline function implemented in C++/C and CUDA.
Currently it may only be used in conjunction with the DeepSMLM package. However we are planning on small standalone
wrapper for Python / MATLAB; this is also the reason why we opted for a separate repository.

## Installation

```
conda install -c haydnspass -c conda-forge spline
```

### Known Limitations

* C++/CUDA implementation is currently not ready for standalone use
* Updated: CUDA supports arbitrary ROI size now. ~~CUDA does not support ROIs bigger than 32 x 32 = 1024 pixels (this is due to the maximum number of threads per block). Please refer to the CPU version in this case~~

### Build and Install Python package for Local Use
Make sure that the cuda compiler is in path, should you want to compile with CUDA acceleleration.
```bash
export CUDACXX=/usr/local/cuda/bin/nvcc  # with CUDA support, possibly subject to CMAKE change.

python setup.py install
```

### Buildwheels
```bash
export CUDACXX=/usr/local/cuda/bin/nvcc  # with CUDA support, possibly subject to CMAKE change.

python setup.py bdist_wheel
```

### Build and Deploy with conda
```bash
# recommended: create a new conda build environment
conda create --name build boa mamba
conda activate build

# navigate to [repo]/conda
cd dist_tools/conda
conda mambabuild -c conda-forge spline
```


### CD
Set `ANACONDA_USER` and `ANACONDA_TOKEN` as GitHub Secrets.
