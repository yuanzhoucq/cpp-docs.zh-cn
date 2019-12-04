---
title: 编译器错误 C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: b781e9f81342f35d66eca222bd338252b739096c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737486"
---
# <a name="compiler-error-c2004"></a>编译器错误 C2004

应输入“defined(id)”

标识符必须出现在括号中，且后接预处理器关键字。

此错误还可能来自于为 Visual Studio .NET 2003 执行的编译器一致性工作：在预处理器指令中缺少括号。 如果预处理器指令中缺少右括号，编译器将生成错误。

## <a name="example"></a>示例

以下示例生成 C2004：

```cpp
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

## <a name="example"></a>示例

可能的解决方法：

```cpp
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```
