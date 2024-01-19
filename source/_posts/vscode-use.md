---
title: vscode-use
date: 2024-01-20 00:35:42
tags:
---

ide 集成开发环境: 对代码有较好的智能提示和相互跳转, 对开发调式有较好的图形化界面支持, 相对比较笨重, 如 IDEA

编辑器: 侧重于文本编辑

vscode 定位是编辑器, 但又比一般的编辑器功能丰富许多

vscode 是由 js 框架 electron 编写的, 自带 js, typeScript 和 nodejs 的语法支持

点左下角的 设置 可以看 键盘快捷方式

CTRL + SHIFT + P 打开命令面板, 一些操作和配置可以在命令面板进行

设置中文语言

在命令面板中输入 configure display language 选择简体中文

转换为大写

选中文本后, 在命令面板输入 transfrom 

用户设置 全局生效

工作区设置, 只针对当前项目, 会覆盖用户设置, 保持在项目的 .vscode/settings.json

设置自动保存

在设置中搜索 files.autosave 选择 afterDelay

输入 ! 再按下 enter 键, 生成 html 骨架

快捷键 CTRL + \, 并排编辑

CTRL + p 快速搜索并打开文件

查看某个函数在哪些地方被调用了

选中函数, 按住 SHIFT + F12

命名重构 F2

CTRL + K 放手再按 Z 进入沉浸式代码

安装 javascript console utils 插件, CTRL + SHIFT + L 生成 console.log()

