# Hardware
Jetson nano

# Install torch
download whl file here : https://drive.google.com/open?id=1h3nsVXskS8yQvLmhrL77m8mImusRy7OR

```bash
sudo apt-get install python3-pip
pip3 install torch-1.0.0a0+8601b33-cp36-cp36m-linux_aarch64.whl
pip3 install numpy
```

# Clone any Pytorch video object detection github repository

pth (which is model file) gonna be hu~ge.So normal git clone are not able to download it. So install git lfs(large file storage)
But i found it unable to download the pth file because the repo ownder didn't purchase some data packs.....
You can download the pth file here https://s3.amazonaws.com/amdegroot-models/ssd300_mAP_77.43_v2.pth
Anyway, here leave the git-lfs installation.
```bash
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash  
sudo apt install git-lfs
```

```bash
git clone https://github.com/yuniktmr/Pytorch-OpenCV-Object-Detection-using-SSD-Convoluted-Neural-Net.git
```
minor changes in this code. In "ssd.py" line 33, change "volatile" to"requires_grad".
And, you should replace the pth file you had just downloaded.

# Install some dependecies using pip3
```bash
pip3 install imageio torchvision imageio-ffmpeg
```
