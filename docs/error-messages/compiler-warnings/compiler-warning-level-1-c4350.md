---
title: 编译器警告（等级 1）C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 8f23751151d8d83c68608d926ef422d56dde41a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384200"
---
# <a name="compiler-warning-level-1-c4350"></a>编译器警告（等级 1）C4350

行为更改: 调用了“member1”而不是“member2”

右值不能绑定到的非常量引用。 在视觉对象的版本C++在 Visual Studio 2003 中之前，可能会将右值绑定到直接初始化中的非常量引用。 此代码将会提供一条警告。

为了向后兼容，仍可以将右值绑定到非常量引用但只要有可能，是首选标准转换。

此警告表示视觉对象中的行为的更改C++.NET 2002年的编译器。 如果启用，此警告可能可能给出有关正确的代码。 例如，它可以为其赋予使用时**std::auto_ptr**类模板。

如果收到此警告，检查你的代码以查看是否这取决于绑定到非常量引用的右值。 将一个常量添加到该引用或提供其他的常量引用重载可能会解决此问题。

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下面的示例生成 C4350:

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```