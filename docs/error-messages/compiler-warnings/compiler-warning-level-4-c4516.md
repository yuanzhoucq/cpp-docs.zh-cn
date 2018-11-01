---
title: 编译器警告（等级 4）C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564042"
---
# <a name="compiler-warning-level-4-c4516"></a>编译器警告（等级 4）C4516

class::symbol： 否决访问声明;成员 using 声明提供更好的选择

ANSI c + + 委员会已经宣布访问声明 (正在更改而无需在派生类中成员的访问权限[使用](../../cpp/using-declaration.md)关键字) 已过期。 C + + 的未来版本可能不支持访问声明。

下面的示例生成 C4516:

```
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