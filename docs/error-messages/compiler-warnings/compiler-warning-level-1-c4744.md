---
title: 编译器警告（等级1） C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f6954ae7966edf200249bb5d10f0dfb011bcef22
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051549"
---
# <a name="compiler-warning-level-1-c4744"></a>编译器警告（等级1） C4744

"var" 在 "file1" 和 "file2" 中具有不同的类型： "type1" 和 "type2"

在两个文件中引用或定义的外部变量在这些文件中具有不同的类型。  若要解决此问题，请使类型定义相同，或者更改其中一个文件中的变量名称。

仅在用/GL 编译文件时发出 C4744  有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
>  C4744 通常出现在 C （不C++）文件中，因为C++在变量名中使用类型信息修饰。  在将示例（以下）编译为C++时，会收到链接器错误 LNK2019。

## <a name="example"></a>示例

此示例包含第一个定义。

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>示例

下面的示例生成 C4744。

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