+++
date = '2025-01-10T12:22:55+08:00'
draft = false
title = 'Docker工作流'
categories = 'Docker'
+++



## 启动Docker容器-docker run

* 启动Docker容器使用`docker run <IMAGE_NAME>:<TAG>` 命令, 有一些常见选项:
  * `--name` : 指定容器的名字, 后面用`docker attach <容器名>`可以直接进入容器.
    * 例如`--name haha`
  * `--network`: 指定容器运行的网络模式, 有三种选项:
    * `--network host`: 容器不会使用虚拟网卡, 而是用Host的IP和端口.
    * `--network bridge`: 默认是`bridge`模式, 容器会被连接到虚拟网卡`docker0`.
  * `-it`: 进入容器后可以通过终端交互.
  * `--rm`: 用`ctrl+d`退出容器后, 立刻删除容器.
  * `--env`: 进入容器后指定环境变量.
  * `-p <host-ip>:<docker-ip>`: 将Host的某个端口和Docker端口绑定, 多个映射需要配置多个`-p`.
  * `-v <host-dir>:<docker-dir>`: 将Host的某个文件映射到Docker上.
  * `-e ENV=<env_value>`: 设置容器启动后的环境变量.
  * `--privileged`: 这个选项能保证如果你在Docker容器中是root, 那么你在Host上也有root权限.



> Docker容器已经启动, 但是忘记映射某些端口/文件, 解决方法:

* 首先停止容器: `docker stop <container>`
* 然后将容器导出为文件: `docker export -o xxx.tar <container>`
* 然后将文件变成镜像: `docker import xxx.tar <image-name>:<tag>`
* 然后重新根据镜像启动容器.



## 容器和本地交换文件

```bash
docker cp 本地路径 <container>:容器路径
docker cp 本地路径 <container>:容器路径
```



## Dockerhub的工作流

* 登陆`Dockerhub`:
  * `docker login`, 然后输入用户名和密码.
  * 如果要求静默模式, 可以使用`docker --username <username> --password <password>`



## 镜像spec-Dockerfile

* 从Dockerfile中构建镜像:

  ```bash
  docker build -t <image-name>:<image-tab> .
  ```

* 如果要把本地的一些文件/文件夹拷贝到Docker, 有两个命令`ADD`和`COPY`

  * 拷贝文件, 直接用`COPY`命令:

    ```dockerfile
    COPY ./.vimrc /root/.vimrc
    ```

  * 拷贝文件夹

* 当在编写Dockerfile时, 不断`docker build`, 如果failed, 可能会产生很多`<none>`镜像, 如果要删除:

  ```bash
   docker rmi $(docker images -f "dangling=true" -q)
  ```

* 删除所有已经Exited的容器:

  ```bash
  docker container prune
  ```

  

