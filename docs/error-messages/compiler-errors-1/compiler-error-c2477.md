---
title: 编译器错误 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 73d8daa9576e4edc29958918c107e9edf18cc579
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447969"
---
# <a name="compiler-error-c2477"></a>编译器错误 C2477

member： 不能通过派生类中初始化静态数据成员

一种模板类的静态数据成员未正确初始化。 这是一项重大更改与版本的 MicrosoftC++在 Visual Studio.NET 2003 中，为了符合 ISO 之前的编译器C++标准。

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