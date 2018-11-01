---
title: 编译器错误 C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 27db194cb308d711a259127b628c60b4d10b94ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458157"
---
# <a name="compiler-error-c2477"></a>编译器错误 C2477

member： 不能通过派生类中初始化静态数据成员

一种模板类的静态数据成员未正确初始化。 这是为了符合 ISO c + + 标准的版本早于 Visual Studio.NET 2003年的 Visual c + + 编译器进行了重大更改。

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