安装：

```bash
sudo apt install docker # 安装默认 docker
# 以下步骤安装支持 nvidia 显卡的 docker 插件
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list \
    | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt update
sudo apt install nvidia-docker2
```

编辑配置文件，使 docker 默认加载 nvidia 插件：

```bash
vi /etc/docker/daemon.json
```

```json
{
  "runtimes": {
    "nvidia": {
      "path": "nvidia-container-runtime",
      "runtimeArgs": []
    }
  },
  "default-runtime": "nvidia"
}
```

下载镜像：
```bash
sudo docker pull ubuntu:16.04
sudo docker pull ubuntu:18.04
```

启动一个镜像为内存中的容器：
```bash

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1Nzk4MTY5MDNdfQ==
-->