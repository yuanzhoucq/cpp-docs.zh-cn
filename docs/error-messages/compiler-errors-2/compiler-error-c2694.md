---
title: 编译器错误 C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4897512f6bd27465b7281d7a27757918128202d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489929"
---
# <a name="compiler-error-c2694"></a>编译器错误 C2694

override： 重写虚函数的限制性异常规范比基类虚拟成员函数 base

重写虚函数，但在[/Za](../../build/reference/za-ze-disable-language-extensions.md)，则重写函数具有限制性较少[异常规范](../../cpp/exception-specifications-throw-cpp.md)。

下面的示例生成 C2694:

```
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```