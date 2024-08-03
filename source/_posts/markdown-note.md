---
title: Markdown 笔记
date: 2023-12-29 15:49:43
tags:
- Markdown
---

# Markdown 笔记

关于 Markdown 的汇总笔记

[TOC]

## Markdown 语法

### 标题

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

```markdown
一级标题, 任意数量的 == 号
====
```

```markdown
二级标题, 任意数量的 -- 号
----
```

### 段落

```markdown
要创建段落, 使用空白行分割.

不要用空格或制表符缩进段落.
```

### 换行

```markdown
在一行末尾加两个或多个空格, 再按回车键,  
即可创建一个换行, 或者直接使用 <br>,
有的编辑器直接回车也可以换行.
```

### 强调

```markdown
**加粗文本(建议)**
__加粗文本__
*斜体*
_斜体_
***加粗的斜体(建议)***
___加粗的斜体___
__*加粗的斜体*__
**_加粗的斜体_**
```

```markdown
~~删除线用两个波浪号~~
```

### 引用

```markdown
> 引用, 可以包含其他 Markdown 元素
>
> 第二段
>> 嵌套引用
```

### 列表

有序列表

```markdown
1. 有序列表
2. 第二行
    1. 四个空格
    2. 嵌套
3. 第三行
    - 嵌套
    - 嵌套
```

无序列表

```markdown
- 无序列表, 破折号/星号/加号都可以, 建议用同一个
* 第二行
    - 嵌套
    - 嵌套
+ 第三行
```

列表嵌套

```markdown
* 在列表中嵌套其他元素

	> 缩进四个空格或一个制表符
	
* 第二行
```

```markdown
* 代码块需要缩进八个空格或两个制表符

		<html>
			<head>
				<title>标题</title>
			</head>
        </html>
        
* 第二行
```

### 代码

```markdown
`代码`
``包裹`反引号`在里面``
```

```markdown
	<html>
		<head>
			<title>创建代码块, 缩进使用四个空格或一个制表符
		<head>
	</html>
```

````markdown
```json
{
	"代码块": ""
}
```
````

### 分隔

```markdown
分隔线, 使用三个星号/破折号/下划线, 建议在分隔线前后加上空白行

***

---

___
```

### 链接

```markdown
[超链接显示名](超链接地址 "超链接title")

直接使用尖括号, 可以将网址和邮箱地址变成链接
<test@qq.com>


链接也可以加强调和斜体等其他元素
**[baidu](https://baidu.com)**

```

锚点

```markdown
### 给标题添加锚点 {#jump}
<a name="jump"> 锚点测试</a>

[按住 Ctrl 点击跳转到锚点](#jump)
[`代码`](#jump)
```

引用

```markdown
[引用链接][1]

[1]: https://www.baidu.com "百度"
```

### 图片

```markdown
![图片alt](图片链接 "图片title")
[![给图片加链接](图片链接 "图片title")](https://www.baidu.com)
```

### 转义

如果不想符号当作元素使用, 在前面使用反斜杠 `\`.

Markdown 会自动转义 `<` 为 `&lt`, 转义 `&` 为  `&amp`.

### 内嵌 HTML 标签

可以直接在 Markdown 里写 HTML 标签.

块级标签如 `<div>` 等, 必须在前后加上空行, 标签也不可以用 tab 或者空格来缩进.

### 表格

使用三个或多个 `---` 创建标题.

```
| 标题 | 标题| 标题|
| :--- | :---: | ---: |
| 左对齐 | 居中 |右对齐 |
```

### 脚注

```markdown
添加脚注.[^1]

[^1]: 这是脚注说明
```

### 勾选框

```markdown
- [x] 勾选
- [ ] 不勾选
```

### Emoji 表情

直接复制表情或者使用[表情简码](https://gist.github.com/rxaviers/7360908)

:tent:

### 参见

* [[Markdown 官方教程](https://markdown.com.cn/)](https://markdown.com.cn/basic-syntax/)

## Markdown 规范

### 文件属性

文件名必须小写, 多个单词用 `-` 分隔

后缀名必须是 `md`

### 文档布局

```markdown
# 文档标题

简要介绍

[TOC]

## 主题

内容

## 参见

* http://www.baidu.com
```

### 文本内容

使用产品/工具和二进制文件的原始名称, 保留大写, 如 `Markdown`.

一行内容限制 80 个字符.

避免使用换行, 而是改为使用段落.

### 列表

对长列表使用惰性编号, Markdown 会正常渲染. 如果列表很小, 也不常修改, 可以使用完整编号.

```markdown
1. 第一行
    1. 嵌套列表使用 4 个空格缩进
    2. 嵌套
1. 第二行
```

如果数据很容易用列表展示, 避免使用表格.

### 表格

```markdown
标题1 | 标题2
---- | ---
香蕉 | 苹果
```

### 代码

```markdown
$ 大多数命令行都是为了粘贴到总端运行 \
  所以使用单个反斜杠换行
```

### 链接

[设置信息丰富的链接标题](https://github.com/google/styleguide/blob/gh-pages/docguide/style.md), 

[长链接或重复链接][放到对于章节或文档的末尾]

[放到对于章节或文档的末尾]: https://github.com/google/styleguide/blob/gh-pages/docguide/style.md
