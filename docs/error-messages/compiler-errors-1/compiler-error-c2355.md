---
title: 编译器错误 C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: e44501f7df05a8b277cd52107ff35c4c4d30578f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759940"
---
# <a name="compiler-error-c2355"></a>编译器错误 C2355

“this”：只能在非静态成员函数或非静态数据成员初始值设定项的内部引用

`this` 指针仅在非静态成员函数或非静态数据成员初始值设定项的内部有效。 当类声明外部的成员函数定义的类范围未正确限定时，可能发生此错误。 当 `this` 指针用于未在类中声明的函数时，也可能发生此错误。

要解决此问题，请确保成员函数定义与类中的成员函数声明匹配，且未声明为静态。 对于数据成员初始值设定项，请确保数据成员未声明为静态。

下面的示例生成 C2355，并演示如何修复此错误：

```cpp
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```
