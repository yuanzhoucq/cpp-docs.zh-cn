---
title: 编译器错误 C3849
ms.date: 11/04/2016
f1_keywords:
- C3849
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
ms.openlocfilehash: 8492f108b57fbc63bd171276b1aa601f96a28b24
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754883"
---
# <a name="compiler-error-c3849"></a>编译器错误 C3849

"type" 类型的表达式中的函数样式调用会丢失所有可用的可用运算符重载的 const 和/或 volatile 限定符

具有指定 const volatile 类型的变量只能调用使用相同或更大的 const volatile 限定定义的成员函数。

若要修复此错误，请提供相应的成员函数。 当转换导致无法进行限定时，不能对 const 或 volatile 限定对象执行转换。 可以获取限定符，但不能在转换中丢失限定符。

以下示例生成 C3849：

```cpp
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
