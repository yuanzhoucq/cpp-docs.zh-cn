---
title: 编译器错误 C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: 80871a73a7c3b4ad04b475539015f85d21ae88b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611271"
---
# <a name="compiler-error-c2355"></a>编译器错误 C2355

“this”：只能在非静态成员函数或非静态数据成员初始值设定项的内部引用

`this` 指针仅在非静态成员函数或非静态数据成员初始值设定项的内部有效。 当类声明外部的成员函数定义的类范围未正确限定时，可能发生此错误。 当 `this` 指针用于未在类中声明的函数时，也可能发生此错误。

要解决此问题，请确保成员函数定义与类中的成员函数声明匹配，且未声明为静态。 对于数据成员初始值设定项，请确保数据成员未声明为静态。

下面的示例生成 C2355，并演示如何修复此错误：

```
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