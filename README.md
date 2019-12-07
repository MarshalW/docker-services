# 基于 docker 的服务

给出一种方案，适合简单有效的在单机上通过多 docker-compose 部署生产环境的多种服务。

## 概述

服务包括：

- nginx 服务，用于做全局的代理
- zentao，禅道服务
- jenkins，jenkins 服务
- phabricator，有关 phabricator 的相关服务
- www，官网 web 页面

运行环境：

- Ubuntu Server 18.04.2
- Docker version 19.03.5
- docker-compose version 1.24.1

### 准备工作

需要在 /etc/hosts 文件中

```
192.168.0.xxx z.myservice
192.168.0.xxx www.myservice
...
```

### 设置环境变量

./nginx/.env.template改名为 ./nginx/.env

设置`PROJECT_HOME=xxx`为项目根目录的绝对路径。

### 启动运行

nginx，启动全局代理：

```
./nginx/docker-compose up -d
```

zentao，启动禅道服务：

```
./zentao/docker-compose up -d
```

浏览器访问:

- www 服务，http://www.myservice
- zentao 服务，http://z.myservice
