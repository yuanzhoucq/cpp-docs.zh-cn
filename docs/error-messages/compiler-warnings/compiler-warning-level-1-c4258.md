---
title: 编译器警告（等级 1）C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a192fb9d8dc046bb3493b90b85371175520ccf95
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230722"
---
# <a name="compiler-warning-level-1-c4258"></a>编译器警告（等级 1）C4258

"variable"：忽略 for 循环中的定义;使用封闭范围中的定义 "

在[/ze](../../build/reference/za-ze-disable-language-extensions.md)和[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)下， [for](../../cpp/for-statement-cpp.md)循环中定义的变量将在循环结束后超出范围 **`for`** 。 如果在包含循环的作用域中再次使用与 loop 变量同名但在封闭循环中定义的变量，则会出现此警告 **`for`** 。 例如：

```cpp
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```
