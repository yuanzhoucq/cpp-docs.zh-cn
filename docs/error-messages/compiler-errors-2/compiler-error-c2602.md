---
title: 编译器错误 C2602
ms.date: 11/04/2016
f1_keywords:
- C2602
helpviewer_keywords:
- C2602
ms.assetid: 6c07a40e-537e-4954-b5c5-1e0e58fe1952
ms.openlocfilehash: da38600ea099c9b0d73e929a100a8c338bd3388f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62215524"
---
# <a name="compiler-error-c2602"></a>编译器错误 C2602

class::Identifier 不是基类 class 的成员

`Identifier` 无法访问，因为它不是继承自任何基类的成员。

下面的示例生成 C2602:

```
// C2602.cpp
// compile with: /c
struct X {
   int x;
};
struct A {
   int a;
};
struct B : public A {
   X::x;   // C2602 B is not derived from X
   A::a;   // OK
};
```