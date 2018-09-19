---
title: 针对函数依赖于自变量名称 (Koenig) 查找 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e71a1fd5a795fb95520ec8d7859e70460a9372c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028813"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>针对函数的依赖于自变量的名称 (Koenig) 查找

编译器可以使用依赖于自变量的名称查找来查找非限定函数调用的定义。 依赖于参数的名称查找也称为 Koenig 查找。 在命名空间、类、结构、联合或模板的层次结构中定义函数调用中每个自变量的类型。 指定未限定[后缀](../cpp/postfix-expressions.md)函数调用中，编译器将搜索与每个自变量类型关联的层次结构中的函数定义的。

## <a name="example"></a>示例

在此示例中，编译器注意到函数 `f()` 采用了参数 `x`。 参数 `x` 是命名空间 `A::X` 中定义的类型 `A`。 编译器搜索命名空间 `A` 并查找采用类型 `f()` 的参数的函数 `A::X` 的定义。

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