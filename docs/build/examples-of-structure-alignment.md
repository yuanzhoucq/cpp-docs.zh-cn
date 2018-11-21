---
title: 结构对齐示例
ms.date: 11/19/2018
helpviewer_keywords:
- structure alignment
- examples [C++], structure alignment
ms.assetid: 03d137bf-5cc4-472e-9583-6498f2534199
ms.openlocfilehash: 7c4b3ae29674e9c4fc27e8e175867339001b9a0d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175335"
---
# <a name="examples-of-structure-alignment"></a>结构对齐示例

以下四个示例每个声明对齐的结构或联合和相应的图形说明了该结构或联合在内存中的布局。 在图中每一列代表一字节的内存，并在列中的数字表示的字节偏移量。 第二行的每个图形中的名称对应于在声明变量的名称。 阴影的列指示填充的所需实现指定的对齐方式。

## <a name="example-1"></a>示例 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD 转换示例 1 结构布局](../build/media/vcamd_conv_ex_1_block.png "AMD 转换示例 1 结构布局")

## <a name="example-2"></a>示例 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD 转换示例 2 结构布局](../build/media/vcamd_conv_ex_2_block.png "AMD 转换示例 2 结构布局")

## <a name="example-3"></a>示例 3

```C
// Total size = 22 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![AMD 转换示例 2 结构布局](../build/media/vcamd_conv_ex_3_block.png "AMD 转换示例 2 结构布局")

## <a name="example-4"></a>示例 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD 转换示例 4 联合 layouit](../build/media/vcamd_conv_ex_4_block.png "AMD 转换示例 4 联合 layouit")

## <a name="see-also"></a>请参阅

[类型和存储](../build/types-and-storage.md)<br/>
