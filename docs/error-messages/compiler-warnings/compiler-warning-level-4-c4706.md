---
title: 编译器警告 （等级 C4706 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843edeaf490f27475003e9303f7929b818e2b104
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036951"
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