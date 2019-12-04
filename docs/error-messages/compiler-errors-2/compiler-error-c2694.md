---
title: 编译器错误 C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: ca378c3e0ce88b454cb89fc08470a277a7be6f47
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755221"
---
# <a name="compiler-error-c2694"></a>编译器错误 C2694

"override"：重写虚函数的限制性异常规范比基类虚成员函数 "base" 少

虚函数已被重写，但在[/za](../../build/reference/za-ze-disable-language-extensions.md)下，重写函数具有限制性较低的[异常规范](../../cpp/exception-specifications-throw-cpp.md)。

下面的示例生成 C2694：

```cpp
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
