---
title: NPM 笔记
date: 2024-01-24 21:41:58
tags:
- NPM
---

# NPM 笔记

关于 NPM 的汇总笔记

[TOC]

## NPM 命令

### 基本命令

```bash
# 查看 NPM 版本
npm -v
# 生成 package.json 文件
npm init
```

### npm config 配置

```bash
# 查看配置
npm config list -l
# 设置模块的全局安装目录
npm conf set prefix 路径
```

### npm info 模块信息

```bash
# 查看模块的信息
npm info hexo
```

### npm search 搜索仓库

```bash
npm search hexo
```

### npm list 列出模块

```bash
# 列出当前项目安装的模块
npm list
# 列出全局安装的模块
npm list -g
```

### npm install 安装模块

```bash
# 安装到当前项目
npm install fluid
# 安装全局模块
npm install -g hexo
```

### npm uninstall 卸载模块

```bash
npm uninstall fluid
# 卸载全局模块
npm uninstall hexo -g
```

### 参见

* [npm 超详细教程](https://segmentfault.com/a/1190000024548728)