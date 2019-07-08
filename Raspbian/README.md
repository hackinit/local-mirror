# Raspbian 镜像源

## 简要说明

这个项目使用 [`apt-mirror`](https://github.com/apt-mirror/apt-mirror) 在 Ubuntu 系统上搭建 Raspbian Jessie Stretch Butler 三个 Release 的镜像源。

镜像源会被储存在 `/mnt/Raspbian` 目录下，建议在 `/mnt` 目录下单独挂载一块硬盘。

## 服务端使用方法

### 安装 apt-mirror

```shell
$ sudo apt-get install -y apt-mirror
```

### 配置

```shell
# 备份原有的 mirror.list
$ sudo mv /etc/apt/mirror.list /etc/apt/mirror.list.bak

# 使用自定义配置
$ sudo cp mirror.list /etc/apt/mirror.list
```

### 开始同步

```shell
$ apt-mirror
```

## 客户端使用方法

### 修改软件源

```shell
$ sudo vim /etc/apt/source.list
```

加入以下内容

```
deb http://<服务器IP>[:PORT]/raspbian/ <Release> main contrib non-free rpi
deb-src http://<服务器IP>[:PORT]/raspbian/ <Release> main contrib non-free rpi

```

### 更新软件源

```shell
$ apt update
```
