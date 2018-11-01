---
title: 编译器警告（等级 1）C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a3ce4c81a86920baddfc1b277df0236a96254be4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478257"
---
# <a name="compiler-warning-level-1-c4258"></a>编译器警告（等级 1）C4258

variable： 从定义忽略 for 循环;使用封闭范围中的定义"

下[/Ze](../../build/reference/za-ze-disable-language-extensions.md)并[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)中, 定义的变量[有关](../../cpp/for-statement-cpp.md)循环之后超出范围**为**循环结束。 如果在作用域包含再次使用循环变量，但在封闭的循环中，定义与同名的变量，会出现此警告**为**循环。 例如：

```
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