---
title: C++ 笔记
date: 2023-12-28 15:09:12
tags: [c++]
---

# 基础

## 简单运行

```cpp
int main()
{
    return 0;
}
```

> VSCODE 快捷键: `ALT + SHIFT + F` 格式化代码

编译

```bash
gcc -o hello hello.c
```

运行

```bash
./hello
```

> CODE RUNNER 快捷键: `CTRL + ALT + N` 运行代码

查看 main 函数的返回值

```bash
echo $?
```

## 简单输入输出

```cpp
#include <iostream>
int main()
{
    // 输出运算符 <<
    // endl 结束当前行, 并刷新缓冲区
    std::cout << "输入 2 个数字: " << std::endl;
    int v1 = 0, v2 = 0;
    // 输入运算符 >>
    std::cin >> v1 >> v2;
    std::cout << v1 << "+" << v2 << "=" << v1 + v2 << std::endl;
    return 0;
}
```

>[解决 code runner 无法输入](https://www.cnblogs.com/yqyang/p/13151160.html)

![Alt text](cpp-note/image.png)

>[解决 code runner 终端乱码](https://blog.csdn.net/qq_43565353/article/details/125782401)

![Alt text](cpp-note/image-1.png)

![Alt text](cpp-note/image-2.png)

```json
chcp 65001;
```