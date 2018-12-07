---
title: 链接器工具错误 LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 8088494106aa702fda0497fa431e48267167a185
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517549"
---
# <a name="linker-tools-error-lnk2004"></a>链接器工具错误 LNK2004

gp 相对链接地址信息溢出以便 target;太大或超出范围，较短的节部分。

部分是太大。

若要解决此错误，请减小的简短的部分中，通过显式将数据放在较长部分通过 #pragma 部分 （".sectionname"，以读取、 写入、 长时间），并使用大小`__declspec(allocate(".sectionname"))`上数据定义和声明。  例如，应用于对象的

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

此外可移动到其自身会是一组数据大于 8 个字节，该编译器将长数据部分中分配的结构以逻辑方式组合数据。  例如，应用于对象的

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };
```

此错误后跟错误`LNK1165`。