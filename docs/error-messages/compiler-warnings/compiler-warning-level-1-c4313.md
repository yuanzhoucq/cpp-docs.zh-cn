---
title: 编译器警告（等级 1）C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 774af2d5d29112d56adf97e22d1bdd758a816ef1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555697"
---
# <a name="compiler-warning-level-1-c4313"></a>编译器警告（等级 1）C4313

“function”：格式字符串中的“格式说明符”与类型“type”的自变量数量发生冲突

指定的格式与要传递的值之间出现冲突。 例如，你将 64 位的参数传递给了未经限定的 %d 格式说明符（预期为一个 32 位的整数参数）。 此警告仅当为 64 位目标编译代码时才会生效。

## <a name="example"></a>示例

以下代码示例在其用于为 64 位目标进行编译时将生成 C4313。

```
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```