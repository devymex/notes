安装
```bash
sudo apt install docker # 安装默认 docker
# 以下步骤安装支持 nvidia 显卡的 docker 插件
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list \
    | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt update
sudo apt install nvidia-docker2
```

下载镜像：
```bash
sudo docker pull ubuntu:16.04
sudo docker pull ubuntu:18.04

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTAzNTk4MzI3XX0=
-->