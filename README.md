# Hardware & Version
Common Desktop
GPU: RTX 2080 Ti
OS: Ubuntu 16.04 LTS
CUDA: 10.0
Python: 3.7

# Install (DO NOT USE ANACONDA!!!!!! STRONGLY RECOMMEND TO INSTALL ON YOUR LOCAL)
## CUDA 10.0
I was CUDA 9.0 .... so clean remove 9.0 and reinstall 10.0


## PyCUDA
```bash
pip install 'pycuda>=2019.1.1' --user
```

## TensorRT version
https://developer.nvidia.com/tensorrt
check your version. I used TensorRT 7.0.0.11 CUDA 10.0 Ubuntu 16.04.
Download from link above

## Unzip
```bash
tar xzvf TensorRT-7.x.x.x ~~~ 
```

## Add Environment Variable
```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<다운로드경로/TensorRT_폴더이름/lib>
# in my case
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/ktk/Desktop/TensorRT-7.0.0.11/lib
```
## install python packages
```bash
# Go to the folder
cd TensorRT-${version}/python
# pip install
sudo pip3 install tensorrt-*-cp3x-none-linux_x86_64.whl
# __in my case (pip directly indicate python3 folder, and 'sudo pip' raise error in my env)__
pip install tensorrt-7.0.0.11-cp37-none-linux_x86_64.whl --user
```

## install UFF packages
```bash
cd TensorRT-${version}/uff
sudo pip3 install uff-0.6.5-py2.py3-none-any.whl
# __in my case (same reason as above)
pip install uff-0.6.5-py2.py3-none-any.whl --user
# when any directory is displayed, success to install
which convert-to-uff 
```

## install graphsurgeon
```bash
cd TensorRT-${version}/graphsurgeon
sudo pip3 install graphsurgeon-0.4.1-py2.py3-none-any.whl
# __in my case (same reason as above)
 pip install graphsurgeon-0.4.1-py2.py3-none-any.whl --user
 ```
 
 ## fastest example to check
 
