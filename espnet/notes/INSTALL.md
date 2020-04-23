# ESPNet Installation
## Requirements
- Python 3.6.10
- gcc 5.4.0
- PyTorch1.0.1
- cmake3.5.1
- CUDA 9.0
- CUDNN 7.0
- Ubuntu 16.04
## Step 1: Setting of the environment for GPU support
- To use cuda (and cudnn), make sure to set paths in your `.bashrc` or `.bash_profile` appropriately.
    ```
    CUDAROOT=/path/to/cuda

    export PATH=$CUDAROOT/bin:$PATH
    export LD_LIBRARY_PATH=$CUDAROOT/lib64:$LD_LIBRARY_PATH
    export CFLAGS="-I$CUDAROOT/include $CFLAGS"
    export CUDA_HOME=$CUDAROOT
    export CUDA_PATH=$CUDAROOT
    ```
- If you want to use multiple GPUs, you should install `nccl` and set paths in your `.bashrc` or `.bash_profile` appropriately, for example:
    ```
    CUDAROOT=/path/to/cuda
    NCCL_ROOT=/path/to/nccl

    export CPATH=$NCCL_ROOT/include:$CPATH
    export LD_LIBRARY_PATH=$NCCL_ROOT/lib/:$CUDAROOT/lib64:$LD_LIBRARY_PATH
    export LIBRARY_PATH=$NCCL_ROOT/lib/:$LIBRARY_PATH
    export CFLAGS="-I$CUDAROOT/include $CFLAGS"
    export CUDA_HOME=$CUDAROOT
    export CUDA_PATH=$CUDAROOT
    ```
    - Note: **ENVIRONMENT** Variable should be set correctly
## Step 2: Install Kaldi
- Detail reference Kaldi Documents
## Step 3: Install Espnet
- Clone espnet
    ```
    $ git clone https://github.com/espnet/espnet
    $ cd espnet
    ```
- Compile
    ```
    $ cd tools
    $ make KALDI=/path/to/kaldi PYTHON_VERSION=3.6 CUDA_VERSION=9.0
    ```