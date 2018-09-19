---
title: 编译器警告 （等级 1） C4350 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad49a7471be257fa0c22f66fa1bb2bbea049194
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096686"
---
# <a name="compiler-warning-level-1-c4350"></a>编译器警告（等级 1）C4350

行为更改: 调用了“member1”而不是“member2”

右值不能绑定到的非常量引用。 在 Visual Studio 2003 之前的 Visual c + + 版本，就可以将右值绑定到直接初始化中的非常量引用。 此代码将会提供一条警告。

为了向后兼容，仍可以将右值绑定到非常量引用但只要有可能，是首选标准转换。

此警告表示从 Visual c + +.NET 2002年编译器行为的更改。 如果启用，此警告可能可能给出有关正确的代码。 例如，它可以为其赋予使用时**std::auto_ptr**类模板。

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