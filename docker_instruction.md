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

启动一个镜像，成为内存中的容器：

```bash
sudo docker run -it -d ubuntu:16.04
```

查询容器列表：

```bash
sudo docker ps
```

进入一个容器：

```bash
sudo docker exec -it <CONTAINER_ID> /bin/bash
```

终止一个容器：

```bash
sudo docker kill <CONTAINER_ID>
```

如果要在容器中访问 nvidia 驱动，需要在容器中设置环境变量：

```bash
container$ export NVIDIA_VISIBLE_DEVICES=all
```

也可以将上述命令加入容器的 `~/.bashrc` ，并执行 `source ~/.bashrc`

将变更后的容器保存为镜像

```bash
sudo docker commit <C>
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyNzk3OTkwMiwyMDY2MTUyNjgwXX0=
-->