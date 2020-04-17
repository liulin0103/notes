---
layout: post
title: 使用nvm管理node环境
date: 2019-01-14 15:23:52
categories:
- 工具
tags:
- node
---



# 使用nvm管理node环境

## 安装nvm

### 安装

两种方式：

cURL:

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
```

Wget:

```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
```

可以在nvm的[release页面](https://github.com/creationix/nvm/releases "release页面")查看最新版本，替换链接中的版本号。

### 配置环境变量

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
```

把上述代码添加到 `~/.zshrc`

记得

```bash
source ~/.zshrc
```

查看nvm版本，验证配置是否成功

```bash
nvm --version
```

## 使用nvm管理node环境

### 安装node

查看远程node版本

```bash
nvm ls-remote
```

安装node

```
nvm install v10.15.0
```

想安装什么版本就安装什么版本，想安装几个就安装几个。

### 切换node版本

查看本地node版本列表

```
nvm ls
```

切换node版本

```
nvm use v10.15.0
```

### 设置默认node版本

如果安装了多个版本的nodeJs可能需要指定default版本.这样每次新打开一个终端都会使用default版本的node

```
nvm alias default v10.15.0
```

## 使用nrm快速切换npm源

有时候需要切换 NPM 镜像。相比每次切换时都手动指定相应参数，使用[nrm](https://github.com/Pana/nrm)要方便的多。

nrm 是一个 NPM 源管理器，允许你快速地在如下 NPM 源间切换：

- [npm](https://www.npmjs.org/)
- [cnpm](http://cnpmjs.org/)
- [strongloop](http://strongloop.com/)
- [european](http://npmjs.eu/)
- [australia](http://npmjs.org.au/)
- [nodejitsu](https://www.nodejitsu.com/)
- [taobao](http://npm.taobao.org/)

### 安装

```sh
npm install -g nrm
```

### 使用

列出可选的源

```sh
nrm ls
```

![](https://lynn-blog-image.oss-cn-shenzhen.aliyuncs.com/2019-01/屏幕快照 2019-01-14 下午3.02.21.png)

带 `*` 的是当前使用的源，上面的输出表明当前源是cnpm源。

切换到taobao

```bash
nrm use taobao
```

增加源

```bash
nrm add  <registry> <url> [home]
```

删除源

```bash
nrm del <registry>
```

测试速度

```bash
nrm test npm  
```

测试所有源响应时间

```bash
nrm test
```

