title: WSL + Docker容器，Windows上最爽的开发体验
author: rdisme
tags:
  - docker
  - wsl
categories:
  - docker
date: 2023-11-21 15:01:00
---
> 为什么爽？举个例子，前端开发，不可避免要解决项目环境不一致的问题，比如每个项目依赖的node版本不一致，常规做法通过nvm等版本管理，这种方式要安装nvm，不同项目要切换版本动作，使用容器化开发，每个项目配置一个compose文件，直接一键启动！

> 更新时间：2023-11-21


1、[WSL安装Ubuntu](https://learn.microsoft.com/en-us/windows/wsl/install)

2、进入Ubuntu，安装docker

```
sudo apt update
sudo apt upgrade
sudo apt install docker.io
sudo service docker start
sudo systemctl enable docker
sudo usermod -aG docker $USER
docker --version

```
3、安装docker-compose


```
// 请将 版本号 替换为你要下载的 Docker Compose 版本（也可以把文件下载下来传到Ubuntu）
sudo curl -L "https://github.com/docker/compose/releases/download/版本号/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

4、配置镜像加速

阿里云加速器：
```
登录阿里云账号，进入 容器镜像服务。
在左侧导航栏中选择 "镜像加速器"。
复制加速器地址。
```

5、打开VScode，wsl连接，写代码

