[[ 简体中文 ]](https://sun-panel-doc.enianteam.com/zh_cn/introduce/project.html) |
[[ English ]](https://sun-panel-doc.enianteam.com/introduce/project.html)

<div align=center>

<img src="./doc/images/logo.png" width="100" height="100" />

# Sun-Panel

[![Github](https://img.shields.io/badge/Github-123456?logo=github&labelColor=242424)](https://github.com/hslr-s/sun-panel)
[![Gitee](https://img.shields.io/badge/Gitee-123456?logo=gitee&labelColor=c71d23)](https://gitee.com/hslr/sun-panel)
[![docker](https://img.shields.io/badge/docker-123456?logo=docker&logoColor=fff&labelColor=1c7aed)](https://hub.docker.com/r/hslr/sun-panel) 
[![Bilibili](https://img.shields.io/badge/Bilibili-123456?logo=bilibili&logoColor=fff&labelColor=fb7299)](https://space.bilibili.com/27407696/channel/collectiondetail?sid=2023810)
[![YouTube](https://img.shields.io/badge/YouTube-123456?logo=youtube&labelColor=ff0000)](https://www.youtube.com/channel/UCKwbFmKU25R602z6P2fgPYg)
<br>
[![GitHub User's stars](https://img.shields.io/github/stars/hslr-s%2Fsun-panel?style=flat&logo=github)](https://github.com/hslr-s/sun-panel)
[![github downloads](https://img.shields.io/github/downloads/hslr-s/sun-panel/total.svg?logo=github)](https://github.com/hslr-s/sun-panel/releases)
[![docker pulls](https://img.shields.io/docker/pulls/hslr/sun-panel.svg?logo=docker)](https://hub.docker.com/r/hslr/sun-panel)

[[ 中文文档 ]](https://sun-panel-doc.enianteam.com/zh_cn) |
[[ Document ]](https://sun-panel-doc.enianteam.com) |
[[ Demo ]](http://sunpaneldemo.enianteam.com) 

Server, NAS navigation panel, Homepage, Browser homepage.
<br>
一个服务器、NAS导航面板、Homepage、浏览器首页。

</div>


## 🧊 最新完整文档（DOC）

[最新完整文档（DOC）](https://sun-panel-doc.enianteam.com/)


## 🎨 演示（demo）

[查看演示站](https://sun-panel-doc.enianteam.com/introduce/demo_site.html)

## 🍜 使用运行教程

<div id="default-username"></div>

### 默认账号密码
账号：admin@sun.cc

密码：12345678

### 命令参数
|参数|说明|
|---|---|
|-h|查看命令说明|
|-config|生成配置文件（conf/conf.ini）|
|-password-reset|重置第一个用户的密码|

### 二进制文件运行

去 [Releases](https://github.com/hslr-s/sun-panel/releases) 下载二进制文件

执行示例

```sh
./sun-panel
```

#### 重置密码

执行示例

```sh
./sun-panel -password-reset
```
输出
```
密码已经重置成功，以下是账号信息
用户名  xxx@qq.com
密码  12345678
```

### docker 运行

目录挂载 `-v`，根据自己的需求选择：
|容器目录|说明|
|---|---|
|/app/conf|配置文件|
|/app/uploads|上传的文件|
|/app/database|数据库文件|
|/app/runtime|运行日志(不推荐挂载)|

1. 拉取镜像
```sh
docker pull hslr/sun-panel
```

2. 直接下载运行
```sh
docker run -d --restart=always -p 3002:3002 \
-v ~/docker_data/sun-panel/conf:/app/conf \
-v ~/docker_data/sun-panel/uploads:/app/uploads \
-v ~/docker_data/sun-panel/database:/app/database \
--name sun-panel \
hslr/sun-panel
```


### 自编译运行

[请参考完整文档](https://sun-panel-doc.enianteam.com/zh_cn/usage/compile.html)
#### 前端
```sh
# 开发运行

pnpm dev

# 编译打包(打包后生成dist目录，若需要结合后端使用请改成web)

pnpm build
```
#### 后端
1.正式编译程序前先进入service
2.按照静态资源编译教程编译后端静态文件
3.正式编译
```sh
进入后端项目
cd service

# 开发运行
go run main.go

# 编译打包
go build -o sun-panel main.go
```
#### docker
WARNING
执行命令前，请保证你已经拉取了项目代码，然后使用命令行进入到项目根目录

构建docker镜像

```sh
docker build -t sun-panel .
```
运行 D:\docker\data\sun-panel 为本地开发运行的路径
```sh
docker run --rm -d -p 3003:3002 -v  D:\docker\data\sun-panel\conf:/app/conf -v  D:\docker\data\sun-panel\runtime:/app/runtime -v D:\docker\data\sun-panel\uploads:/app/uploads -v D:\docker\data\sun-panel\database:/app/database --name sun-panel sun-panel
```
