---
title: 针对函数的依赖于自变量的名称 (Koenig) 查找
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 88811e8070fdfe398bc12734221dee772515d8bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190530"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>针对函数的依赖于自变量的名称 (Koenig) 查找

编译器可以使用依赖于自变量的名称查找来查找非限定函数调用的定义。 依赖于自变量的名称查找也称为 Koenig 查找。 在命名空间、类、结构、联合或模板的层次结构中定义函数调用中每个自变量的类型。 当指定非限定[后缀](../cpp/postfix-expressions.md)函数调用时，编译器将在与每个参数类型关联的层次结构中搜索函数定义。

## <a name="example"></a>示例

在此示例中，编译器注意到函数 `f()` 采用了自变量 `x`。 自变量 `x` 是命名空间 `A::X` 中定义的类型 `A`。 编译器搜索命名空间 `A` 并查找采用类型 `f()` 的参数的函数 `A::X` 的定义。

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```
