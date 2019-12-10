---
title: 编译器警告（等级 4）C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: 2ff8794dcf29539b492f53bfdf6f0810988c0f72
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989905"
---
# <a name="compiler-warning-level-4-c4706"></a>编译器警告（等级 4）C4706

条件表达式内的赋值

条件表达式中的测试值是赋值的结果。

赋值包含一个值（赋值左侧的值），可以在其他表达式（包括测试表达式）中合法使用该值。

下面的示例生成 C4706：

```cpp
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

即使在测试条件两边加两个括号，也会出现此警告：

```cpp
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

如果打算测试关系而不进行赋值，请使用 `==` 运算符。 例如，下面的行测试和 b 是否相等：

```cpp
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

如果要使测试值成为赋值的结果，请测试以确保赋值非零或非 null。 例如，下面的代码不会生成此警告：

```cpp
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
