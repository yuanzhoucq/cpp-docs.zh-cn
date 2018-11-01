---
title: 编译器警告（等级 4）C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: e57470fcd8e7b014084b094c9ca5e39f0a86d85e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630014"
---
# <a name="compiler-warning-level-4-c4706"></a>编译器警告（等级 4）C4706

条件表达式内的赋值

条件表达式中的测试值已分配的结果。

分配有一个值 （在赋值语句左侧的值），可以在另一个表达式，包括测试表达式中合法使用。

下面的示例生成 C4706:

```
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

即使两个测试条件两边的括号，则将出现警告：

```
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

如果您的意图是测试某一关系并不进行分配，请使用`==`运算符。 例如，下行将测试和 b 相等：

```
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

如果你想要将测试值分配的结果，测试以确保分配非零值且不为 null。 例如，下面的代码将生成此警告：

```
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```