---
title: 编译器警告（等级 4）C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 47e278bbc69b972f6acc391d6b3278ab8d159c08
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990700"
---
# <a name="compiler-warning-level-4-c4516"></a>编译器警告（等级 4）C4516

"class：： symbol"：已弃用访问声明;成员 using 声明提供更好的替代方法

ANSI C++委员会已声明访问声明（在不[使用 using](../../cpp/using-declaration.md)关键字的情况下更改派生类中成员的访问权限）已过时。 的C++未来版本可能不支持访问声明。

下面的示例生成 C4516：

```cpp
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```
