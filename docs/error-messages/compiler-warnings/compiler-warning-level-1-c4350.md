---
title: 编译器警告（等级 1）C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187214"
---
# <a name="compiler-warning-level-1-c4350"></a>编译器警告（等级 1）C4350

行为更改: 调用了“member1”而不是“member2”

右值不能绑定到非常量引用。 在 Visual Studio 2003 C++之前的 Visual visual Studio 版本中，可以在直接初始化中将右值绑定到非常量引用。 此代码现在提供警告。

为实现向后兼容性，仍可以将右绑定到非常量引用，但如果可能，应首选标准转换。

此警告表示 Visual C++ .net 2002 编译器的行为发生了更改。 如果启用，可能会为正确的代码提供此警告。 例如，在使用**std：： auto_ptr**类模板时，可以提供此方法。

如果收到此警告，请检查代码以查看它是否依赖于将右绑定到非常量引用。 向引用添加 const 或提供附加的 const 引用重载可以解决此问题。

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下面的示例生成 C4350：

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
