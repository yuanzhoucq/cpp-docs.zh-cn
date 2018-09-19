---
title: 编译器错误 C3849 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3849
dev_langs:
- C++
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08f89deb3bd83162dd7cf5dc80335e5274efa1c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077498"
---
# <a name="compiler-error-c3849"></a>编译器错误 C3849

表达式中的类型 type 的函数样式调用会失去所有数字可用运算符重载的 const 和/或 volatile 限定符

使用指定的量可变类型的变量可以仅调用成员函数定义有相同或更大的量可变限定。

若要解决此错误，请提供相应的成员函数。 转换导致丢失限定时，不能 const 或 volatile 限定的对象上执行转换。 您可以获得限定符，但不能丢失在转换中的限定符。

以下示例生成 C3849:

```
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```