---
title: 编译器警告（等级 1）C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 2118a32af8b99d35c1e1a6691561391ec5d2b8cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385415"
---
# <a name="compiler-warning-level-1-c4744"></a>编译器警告（等级 1）C4744

var 具有 file1 和 file2 中的不同类型: type1 和 type2

在两个文件中定义或引用的外部变量在这些文件中具有不同类型。  若要解决，请将类型定义相同，或者更改变量名称中的文件之一。

仅当文件使用 /gl 进行编译时，发出 C4744  有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
>  C4744，通常会出现在 C 中 (不C++) 文件，因为在C++变量的名称修饰的类型信息。  （下面） 的示例时编译为C++，则会收到链接器错误 LNK2019。

## <a name="example"></a>示例

此示例包含的第一个定义。

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>示例

下面的示例生成 C4744。

```
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```