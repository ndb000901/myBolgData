---
title: C语言程序里全局变量、局部变量、堆、栈
tags:
    - C
---
## C语言程序里全局变量、局部变量、堆、栈

**1.实验环境**
>1.ubuntu20


**全局变量、静态局部变量保存在全局数据区，初始化的和未初始化的分别保存在一起。普通局部变量保存在堆栈中。
在C\C++中，通常可以把内存理解为4个分区：栈、堆、全局/静态存储区和常量存储区**

>1.内存栈区stack： 存放局部变量名；
>
>2.内存堆区heap： 存放new或者malloc出来的对象；
>
>3.Text & Data & Bss：代码段与静态分配
>
>4.BSS区（未初始化数据段）：并不给该段的数据分配空间，仅仅是记录了数据所需空间的大小。
>
>5.DATA（初始化的数据段）：为数据分配空间，数据保存在目标文件中。

<!--more-->

**2.源码**

haha.c
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
void before()
{
}
char g_buf[16];
char g_buf2[16];
char g_buf3[16];
char g_buf4[16];
char g_i_buf[]="123";
char g_i_buf2[]="123";
char g_i_buf3[]="123";
void after()
{
}
int main(int argc, char **argv)
{
        char l_buf[16];
        char l_buf2[16];
        char l_buf3[16];
        static char s_buf[16];
        static char s_buf2[16];
        static char s_buf3[16];
        char *p_buf;
        char *p_buf2;
        char *p_buf3;
        
        p_buf = (char *)malloc(sizeof(char) * 16);
        p_buf2 = (char *)malloc(sizeof(char) * 16);
        p_buf3 = (char *)malloc(sizeof(char) * 16);
 
        printf("g_buf: 0x%x\n", g_buf);
        printf("g_buf2: 0x%x\n", g_buf2);
        printf("g_buf3: 0x%x\n", g_buf3);
        printf("g_buf4: 0x%x\n", g_buf4);
 
        printf("g_i_buf: 0x%x\n", g_i_buf);
        printf("g_i_buf2: 0x%x\n", g_i_buf2);
        printf("g_i_buf3: 0x%x\n", g_i_buf3);
 
        printf("l_buf: 0x%x\n", l_buf);
        printf("l_buf2: 0x%x\n", l_buf2);
        printf("l_buf3: 0x%x\n", l_buf3);
 
        printf("s_buf: 0x%x\n", s_buf);
        printf("s_buf2: 0x%x\n", s_buf2);
        printf("s_buf3: 0x%x\n", s_buf3);
 
        printf("p_buf: 0x%x\n", p_buf);
        printf("p_buf2: 0x%x\n", p_buf2);
        printf("p_buf3: 0x%x\n", p_buf3);
 
        printf("before: 0x%x\n", before);
        printf("after: 0x%x\n", after);
        printf("main: 0x%x\n", main);
 
        if (argc > 1)
        {
                strcpy(l_buf, argv[1]);
        }
        return 0;
}

```

**3.效果**

![image](https://user-images.githubusercontent.com/48900845/112803918-6184dc00-90a6-11eb-913e-1ae3d29d7102.png)

>作者info
>
>作者：DebugWuhen
>
>原创公众号：『DebugWuhen』，专注于记录有趣的编程技术和有益的程序人生，期待你的关注。
>
>转载说明：务必注明来源（注明：来源于公众号：DebugWuhen， 作者：DebugWuhen）
>
>![image](https://user-images.githubusercontent.com/48900845/112752163-3b0e6480-9004-11eb-899d-66ddef749c2b.png)
