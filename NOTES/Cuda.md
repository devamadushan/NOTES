
Ubuntu :
sudo apt update && sudo apt upgrade -y
ubuntu-drivers devices
	- reperer le driver necessaire 
sudo apt install -y nvidia-driver-550
sudo modprobe nvidia : 
reboot d'aboord 
nvidia-smi
```
(.venv) deva@Deva:~/octopus_brain$ nvidia-smi
Thu Jan 30 11:32:42 2025       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.120                Driver Version: 550.120        CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA T600 Laptop GPU         Off |   00000000:01:00.0 Off |                  N/A |
| N/A   56C    P0             10W /   35W |       5MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      5277      G   /usr/lib/xorg/Xorg                              4MiB |
+-----------------------------------------------------------------------------------------+
(.venv) deva@Deva:~/octopus_brain$ 

```

Installer cuda 

wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb
sudo dpkg -i cuda-keyring_1.0-1_all.deb

sudo apt install -y cuda

 nvcc --version

debian :

sudo apt update && sudo apt upgrade -y
lspci | grep -i nvidia
nvidia-smi

---

lspci | grep -i nvidia
