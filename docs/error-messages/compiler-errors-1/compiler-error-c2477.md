---
title: 编译器错误 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 27db194cb308d711a259127b628c60b4d10b94ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383225"
---
# <a name="compiler-error-c2477"></a>编译器错误 C2477

member： 不能通过派生类中初始化静态数据成员

一种模板类的静态数据成员未正确初始化。 这是一项重大更改与视觉对象的版本C++在 Visual Studio.NET 2003 中，为了符合 ISO 之前的编译器C++标准。

下面的示例生成 C2477:

```
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