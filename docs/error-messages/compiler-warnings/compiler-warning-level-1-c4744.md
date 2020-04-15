---
title: 编译器警告（等级 1）C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367383"
---
# <a name="compiler-warning-level-1-c4744"></a>编译器警告（等级 1）C4744

"var"在"file1"和"file2"中有不同的类型："类型 1"和"类型 2"

在两个文件中引用或定义的外部变量在这些文件中具有不同的类型。  要解决，请使类型定义相同，或更改其中一个文件中的变量名称。

仅当使用 /GL 编译文件时，才会发出 C4744。  有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
> C4744 通常发生在 C（不是C++）文件中，因为在C++变量名称用类型信息修饰。  当示例（下图）编译为C++时，您将获得链接器错误 LNK2019。

## <a name="example"></a>示例

此示例包含第一个定义。

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>示例

以下示例生成 C4744。

```c
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
