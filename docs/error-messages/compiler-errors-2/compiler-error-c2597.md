---
title: 编译器错误 C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: 680268948f8642b02768bd4b3092666982e14eb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759303"
---
# <a name="compiler-error-c2597"></a>编译器错误 C2597

对非静态成员“identifier”的非法引用

可能的原因：

1. 在静态成员函数中指定了非静态成员。 若要访问非静态成员，必须传入或创建类的本地实例并使用成员访问运算符（`.` 或 `->`）。

1. 指定标识符不是类、结构或联合的成员。 检查标识符拼写。

1. 成员访问运算符引用非成员函数。

1. 下面的示例生成 C2597，并演示如何修复此错误：

```cpp
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```
