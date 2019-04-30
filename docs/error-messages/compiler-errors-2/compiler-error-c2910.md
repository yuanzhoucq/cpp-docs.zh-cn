---
title: 编译器错误 C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 58d56ad834b34425cda4ac7ba081eabd2424e451
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408350"
---
# <a name="compiler-error-c2910"></a>编译器错误 C2910

function： 不能显式专用化

编译器检测到尝试两次显式专用化函数。

下面的示例生成 C2910:

```
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

如果你尝试显式专用化非模板成员，则还可以生成 C2910。 也就是说，您可以仅显式特殊化函数模板。

下面的示例生成 C2910:

```
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

此错误还将生成的 Visual Studio.NET 2003年执行的编译器一致性工作:。

代码将视觉对象的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中有效C++，删除`template <>`。

下面的示例生成 C2910:

```
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```