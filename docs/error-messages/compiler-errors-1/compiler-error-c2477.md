---
title: 编译器错误 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: aa276ea839f11574609b183d78b46e08581a1b51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743648"
---
# <a name="compiler-error-c2477"></a>编译器错误 C2477

"member"：静态数据成员不能通过派生类初始化

模板类的静态数据成员未正确初始化。 这是对 Visual Studio .NET 2003 之前的 Microsoft C++编译器版本的重大更改，以便符合 ISO C++标准。

下面的示例生成 C2477：

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
