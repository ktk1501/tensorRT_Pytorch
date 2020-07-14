### clean uninstall

https://teddylee777.github.io/linux/CUDA-%EC%9D%B4%EC%A0%84%EB%B2%84%EC%A0%84-%EC%82%AD%EC%A0%9C%ED%9B%84-%EC%9E%AC%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0

install graphic driver 410 cuda10.0 and cudnn 7.4.2 
(https://gist.github.com/matheustguimaraes/43e0b65aa534db4df2918f835b9b361d)
### Install the latest NVIDIA driver
Update package lists, download and install NVIDIA driver
```
sudo apt-get update
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt install nvidia-410
```

#### Reboot
Restart the computer
```
reboot
```

#### Testing
Lets test if all worked well
```
nvidia-smi
```

#### Download CUDA Toolkit
Download the CUDA Toolkit here (which fit my PC)

https://developer.nvidia.com/cuda-10.0-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=runfilelocal

or on NVIDIA official website (many options here)
https://developer.nvidia.com/cuda-downloads


#### Go to the download folder
After download the file, go to the download folder:
```
cd Downloads
```

#### Run the file
```
sudo sh cuda_10.0.130_410.48_linux.run
```


You have to make some choices in the terminal:

- Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 384.81? ``` n ```
- Install the CUDA 10.0 Toolkit? ``` y ```
- Do you want to install a symbolic link at /usr/local/cuda? ``` y ```
- Install the CUDA 10.0 Samples? ``` y ```

Leave the rest as default. ``` ENTER ```

### Testing
Let's test if everything worked well
```
cd /usr/local/cuda/samples
sudo make -k
./deviceQuery
```
If appears something like:
```
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "GeForce MX130"
  CUDA Driver Version / Runtime Version          10.0 / 10.0
  CUDA Capability Major/Minor version number:    5.0
  Total amount of global memory:                 2004 MBytes (2101870592 bytes)
  ( 3) Multiprocessors, (128) CUDA Cores/MP:     384 CUDA Cores
  GPU Max Clock rate:                            1189 MHz (1.19 GHz)
  Memory Clock rate:                             2505 Mhz
  Memory Bus Width:                              64-bit
  L2 Cache Size:                                 1048576 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65536), 3D=(4096, 4096, 4096)
  Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 1 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device supports Compute Preemption:            No
  Supports Cooperative Kernel Launch:            No
  Supports MultiDevice Co-op Kernel Launch:      No
  Device PCI Domain ID / Bus ID / location ID:   0 / 1 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 10.0, CUDA Runtime Version = 10.0, NumDevs = 1
Result = PASS
```
The library was installed!

## Install cuDNN
### Download cuDNN v7.4.2 (Dec 14, 2018), for CUDA 10.0
Download the cuDNN on NVIDIA official website
https://developer.nvidia.com/cudnn

NOTE: *You have to sign up at NVIDIA website before*

Download the three packages:
- cuDNN Runtime Library for Ubuntu16.04 (Deb)
- cuDNN Developer Library for Ubuntu16.04 (Deb)
- cuDNN Code Samples and User Guide for Ubuntu16.04 (Deb)

### Go to downloads folder
```
cd Downloads
```

### Install the .deb packages
```
sudo dpkg -i libcudnn7_7.4.2.24-1+cuda10.0_amd64.deb
sudo dpkg -i libcudnn7-dev_7.4.2.24-1+cuda10.0_amd64.deb 
sudo dpkg -i libcudnn7-doc_7.4.2.24-1+cuda10.0_amd64.deb
```

### Export CUDA path
```
export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64:$LD_LIBRARY_PATH
export PATH=/usr/local/cuda-10.0/bin:$PATH
```

### Reload bash
```
source ~/.bashrc
```

### Testing
Go in your ```/usr/src``` and copy the 'cudnn_samples_v7' to any folder you want,
to test if all worked well. In my case, I paste it in 'Desktop' folder.

```
cd Desktop/cudnn_samples_v7/mnistCUDNN/
make clean && make
./mnistCUDNN
```

If appears something like:

```
cudnnGetVersion() : 7402 , CUDNN_VERSION from cudnn.h : 7402 (7.4.2)
Host compiler version : GCC 5.4.0
There are 1 CUDA capable devices on your machine :
device 0 : sms  3  Capabilities 5.0, SmClock 1189.0 Mhz, MemSize (Mb) 2004, MemClock 2505.0 Mhz, Ecc=0, boardGroupID=0
Using device 0

Testing single precision
Loading image data/one_28x28.pgm
Performing forward propagation ...
Testing cudnnGetConvolutionForwardAlgorithm ...
Fastest algorithm is Algo 1
Testing cudnnFindConvolutionForwardAlgorithm ...
^^^^ CUDNN_STATUS_SUCCESS for Algo 0: 0.034528 time requiring 0 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 1: 0.038624 time requiring 3464 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 2: 0.040992 time requiring 57600 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 4: 0.174656 time requiring 207360 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 7: 0.440832 time requiring 2057744 memory
Resulting weights from Softmax:
0.0000000 0.9999399 0.0000000 0.0000000 0.0000561 0.0000000 0.0000012 0.0000017 0.0000010 0.0000000 
Loading image data/three_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000000 0.0000000 0.9999288 0.0000000 0.0000711 0.0000000 0.0000000 0.0000000 0.0000000 
Loading image data/five_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000008 0.0000000 0.0000002 0.0000000 0.9999820 0.0000154 0.0000000 0.0000012 0.0000006 

Result of classification: 1 3 5

Test passed!

Testing half precision (math in single precision)
Loading image data/one_28x28.pgm
Performing forward propagation ...
Testing cudnnGetConvolutionForwardAlgorithm ...
Fastest algorithm is Algo 1
Testing cudnnFindConvolutionForwardAlgorithm ...
^^^^ CUDNN_STATUS_SUCCESS for Algo 0: 0.036960 time requiring 0 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 1: 0.051584 time requiring 3464 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 2: 0.066176 time requiring 28800 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 4: 0.199936 time requiring 207360 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 7: 0.516160 time requiring 2057744 memory
Resulting weights from Softmax:
0.0000001 1.0000000 0.0000001 0.0000000 0.0000563 0.0000001 0.0000012 0.0000017 0.0000010 0.0000001 
Loading image data/three_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000000 0.0000000 1.0000000 0.0000000 0.0000714 0.0000000 0.0000000 0.0000000 0.0000000 
Loading image data/five_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000008 0.0000000 0.0000002 0.0000000 1.0000000 0.0000154 0.0000000 0.0000012 0.0000006 

Result of classification: 1 3 5

Test passed!
```
You installed it everything with great success.

Everything is ready for you to use the GPU and do great things.

Have a nice day!
