---
title: "C 位域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "位域"
  - "位域"
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 位域
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了结构或联合的成员的声明符外，结构声明符也可能是指定数目的位，称为“位域”。其长度从字段名称的声明符到冒号。  位域被解释为整型。  
  
## 语法  
 *结构声明符*  
 *声明符*  
  
 *类型说明符说明符* 选择               **：** *常数表达式*  
  
 *constant\-expression* 指定在位字段宽度。  `declarator` 的“类型说明符”必须是 `unsigned int`、**signed int** 或 `int`，而且“常数表达式”必须是非负整数值。  如果该值为零，则声明没有`declarator`。  不允许位域的数组、指向位域的指针和函数返回位域。  可选 `declarator` 命名位域。  位域只能声明为结构的一部分。  该 address\-of 运算符 \(**&**\) 不能被用于位元\-字段组件。  
  
 未命名位域不可引用，且其内容在运行时是不可预测的。  它们可以出于对齐目的用作“虚拟”字段。  指定了宽度为 0 的一个未命名的位域确保跟在其后在“结构声明列表”的成员的存储在 `int` 边界开始。  
  
 位域还必须足够长以包含该位模式。  例如，这两种两个语句均不合法：  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
 此示例定义名为 `screen` 的二维结构数组。  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
 数组包含 2000 个元素的。  每个元素都是包含四位字段成员的单个结构：`icon`、 `color`、 `underline`和 `blink`。  每个结构的大小是两个字节。  
  
 位域与整数类型有相同的语义。  这意味着位域在表达式中使用方式与同样基类型使用变量的方式完全相同，无论有多少数位在位域。  
  
 **Microsoft 专用**  
  
 定义为 `int` 的位域被视为带符号的位域。  ANSI C 标准的 Microsoft 扩展允许位域的 `char` 和 **long** 类型（**signed** 和 `unsigned`）。  带有基类型**"长"**,**"短"**，或`char` \(**“已签名“**或 `unsigned`\)的未命名位域强制对齐为边界合适到基类型。  
  
 在整数中按照从最不重要到最重要的位的顺序来分配位域。  在以下代码  
  
```  
struct mybitfields  
{  
    unsigned short a : 4;  
    unsigned short b : 5;  
    unsigned short c : 7;  
} test;  
  
int main( void );  
{  
    test.a = 2;  
    test.b = 31;  
    test.c = 0;  
}  
```  
  
 该位按如下所示排列:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 虽然 8086 处理器的系列在高字节前存储整数值的低字节，上面的整数 `0x01F2` 将被作为由`0x01`紧随的`0xF2` 存储到物理内存中。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [结构声明](../c-language/structure-declarations.md)