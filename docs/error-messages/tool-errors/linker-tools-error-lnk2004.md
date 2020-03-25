---
title: 链接器工具错误 LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 0d26ab12c5b82d52b7dcbb176d9bfa033d7ddfee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194832"
---
# <a name="linker-tools-error-lnk2004"></a>链接器工具错误 LNK2004

"target" 的 gp 相对链接地址信息溢出;short 部分 "部分" 太大或超出范围。

部分太大。

若要解决此错误，请减小 short 部分的大小，方法是将数据通过 #pragma 部分（"sectionname"、"读取"、"写入"、"long"）和 "对数据定义和声明使用 `__declspec(allocate(".sectionname"))`" 显式放置。  例如，

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

您还可以将逻辑分组的数据移到其自身的结构中，该结构将是大于8字节的数据集合，编译器将在长数据部分中分配。  例如，

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

此错误后跟严重错误 `LNK1165`。
