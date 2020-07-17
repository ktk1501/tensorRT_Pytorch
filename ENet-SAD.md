## How to run
### Update Nvidia graphic driver
I updated graphic driver to 'nvidia-450.51.05'. Other dependencies are same as [README.md](README.md).

### PIP packages
Just few pip installed packages like torchvision. Simply run 'ENet-SAD_video.py'.

## Performance
(20.07.18.) I am using 'exp1_best.pth'. The average performance is as below:

|  | gpu_runtime | total_runtime |
|---|:---:|---:|
| FPS | 58 | 38 |

|GPU  | RTX 2080 Ti |
|---|:---:|
| CPU | Intel i7-8700 @ 3.20GHz |
| CUDA | 10.0 |
| CuDNN | 7.6.5.32|
