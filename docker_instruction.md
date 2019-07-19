安装
```bash
sudo apt install docker
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list \
    | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt update
sudo apt install nvidia-docker2

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE0NTQzNjY2N119
-->