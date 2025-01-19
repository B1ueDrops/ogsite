+++
date = '2025-01-10T12:22:55+08:00'
draft = false
title = 'Docker的正确使用'
categories = 'Docker'
+++



## 下载依赖

* 下载的第一步, 你需要先移除可能和Docker官方有冲突的一些库, 包括:

  * `docker.io`: 这个是Ubuntu官方维护的的Docker, 可以通过`sudo apt install docker.io`下载, 但是版本一般落后于最新的Docker.
  * `podman-docker`: docker作为前端, 但是后端使用的是`podman`, 无守护进程.
  * 

  * 直接一行命令:

    ```bash
    for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
    ```

* **<font color=red>注意: Docker版本如果过低, 在Docker中运行可能会出现各种错误, 所以遇到问题可以想一下是否是Docker版本.</font>**
  * 因为OS内部的系统调用会随着OS版本不同而不同, Docker内部的系统调用会被捕获, 如果Docker版本过低可能无法处理.



## docker run

* 启动Docker容器使用`docker run <IMAGE_NAME>:<TAG>` 命令, 有一些常见选项:
  * `--name` : 指定容器的名字, 后面用`docker attach <容器名>`可以直接进入容器.
    * 例如`--name haha`
  * `--network`: 指定容器运行的网络模式, 有三种选项:
    * `--network host`: 容器不会使用虚拟网卡, 而是用Host的IP和端口.
    * `--network bridge`: 默认是`bridge`模式, 容器会被连接到虚拟网卡`docker0`.
  * `-it`: 进入容器后可以通过终端交互.
  * `--rm`: 用`ctrl+d`退出容器后, 立刻删除容器.
  * `-p <host-ip>:<docker-ip>`: 将Host的某个端口和Docker端口绑定, 多个映射需要配置多个`-p`.
  * `-v <host-dir>:<docker-dir>`: 将Host的某个文件映射到Docker上.
  * `-e ENV=<env_value>`: 设置容器启动后的环境变量.
  * `--privileged`: 这个选项能保证如果你在Docker容器中是root, 那么你在Host上也有root权限.
    * 如果你要把本地, 只有root能操作的文件映射到docker, 就必须加.



> Docker容器已经启动, 但是忘记映射某些端口/文件, 解决方法:

* 首先停止容器: `docker stop <container>`
* 然后将容器导出为文件: `docker export -o xxx.tar <container>`
* 然后将文件变成镜像: `docker import xxx.tar <image-name>:<tag>`
* 然后重新根据镜像启动容器.



## docker cp

```bash
docker cp 本地路径 <container>:容器路径
docker cp 本地路径 <container>:容器路径
```





## docker build

* 从Dockerfile中构建镜像:

  ```bash
  docker build -t <image-name>:<image-tab> .
  ```



## docker rmi

* 删除某个镜像:

  ```bash
  docker rmi <image-name>:<tag>
  ```

* 删除所有`None`镜像:

  ```bash
   docker rmi $(docker images -f "dangling=true" -q)
  ```



## docker rm 

* 删除某个容器:

  ```bash
  docker rm <容器名字/ID>
  ```

  

## docker container

* 删除所有已经Exited的容器:

  ```bash
  docker container prune
  ```

  

## Dockerfile

* 把本地文件拷贝到Docker, 直接用`COPY`命令:

  ```dockerfile
  COPY ./.vimrc /root/.vimrc
  ```

