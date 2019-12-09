---
title: 编译器错误 C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 0061a7171dd08440ec5d8c8b8cadb77303ff8f41
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761110"
---
# <a name="compiler-error-c2910"></a>编译器错误 C2910

"function"：不能显式专用化

编译器检测到对函数进行显式专用化的尝试两次。

下面的示例生成 C2910：

```cpp
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

如果尝试显式专用化非模板成员，还可以生成 C2910。 也就是说，只能显式专用化函数模板。

下面的示例生成 C2910：

```cpp
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

此错误还会由于在 Visual Studio .NET 2003 中完成的编译器一致性工作而生成：。

要使代码在 visual Studio .NET 2003 和 visual Studio .NET 版本的视觉C++对象中有效，请删除 `template <>`。

下面的示例生成 C2910：

```cpp
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
