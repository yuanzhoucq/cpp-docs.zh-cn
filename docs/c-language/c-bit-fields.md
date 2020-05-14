---
title: C 位域
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
ms.openlocfilehash: 62c982fa078182cb1902b6770f0a3713ca4ff7a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326490"
---
# <a name="c-bit-fields"></a>C 位域

除了结构或联合的成员的声明符外，结构声明符也可以是指定数目的位，称为“位域”。 其长度从字段名称的声明符到冒号。 位域被解释为整型类型。

## <a name="syntax"></a>语法

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>opt</sub> **:** *constant-expression*

 constant-expression 指定域的宽度（以位为单位）。 `declarator` 的 type-specifier  必须为 `unsigned int`、signed int  或 `int`，而且 constant-expression  必须为非负整数值。 如果值为零，则声明没有任何 `declarator`。 不允许位域的数组、指向位域的指针和返回位域的函数。 可选的 `declarator` 命名位域。 位域只能声明为结构的一部分。 Address-of 运算符 (&  ) 不能应用于位域组件。

未命名位域不可引用，且其内容在运行时是不可预测的。 它们可以出于对齐目的用作“虚拟”字段。 宽度指定为 0 的未命名位域确保在  struct-declaration-list 中跟在其后的成员的存储在 `int` 边界开始。

位域还必须足够长以包含该位模式。 例如，以下两个语句均不合法：

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

以下示例定义了一个名为 `screen` 的二维结构数组。

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

该数组包含 2,000 个元素。 每个元素都是包含以下四个位域成员的单个结构：`icon`、`color`、`underline` 和 `blink`。 每个结构的大小是两个字节。

位域与整数类型具有相同的语义。 这意味着位域在表达式中的使用方式与同样基类型使用变量的方式完全相同，无论位域中有多少位。

**Microsoft 专用**

定义为 `int` 的位域被视为带符号的位域。 ANSI C 标准的 Microsoft 扩展允许位域的 `char` 和 long  类型（  signed 和 `unsigned`）。 带有基类型 long  、short  或 `char`（signed  或 `unsigned`）的未命名位域强制与适于基类型的边界对齐。

在整数中按照从最高有效位到最低有效位的顺序来分配位域。 在以下代码中

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

这些位将按如下所示排列：

```
00000001 11110010
cccccccb bbbbaaaa
```

由于 8086 系列处理器将整数值的低字节存储在高字节之前，因此上面的整数 `0x01F2` 将按 `0xF2` 后跟 `0x01` 的形式存储在物理内存中。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[结构声明](../c-language/structure-declarations.md)
