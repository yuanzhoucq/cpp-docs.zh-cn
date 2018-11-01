---
title: 编译器警告（等级 1）C4553
ms.date: 11/04/2016
f1_keywords:
- C4553
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
ms.openlocfilehash: 7a299d4a99818699e9be31e7d15d9e589de05c15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470338"
---
# <a name="compiler-warning-level-1-c4553"></a>编译器警告（等级 1）C4553

operator： 运算符不起任何作用;是否要使用 operator？

如果表达式语句作为表达式的顶部具有一个没有任何副作用的运算符，它可能是一个错误。

下面的示例生成 C4553:

```
// C4553.cpp
// compile with: /W1
int func()
{
   return 0;
}

int main()
{
   int i;
   i == func();   // C4553
   // try the following line instead
   // i = func();
}
```