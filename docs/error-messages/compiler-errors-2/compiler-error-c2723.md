---
title: 编译器错误 C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: bc07a99f12ed0e447427990969e54f7f3d3d3b7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635379"
---
# <a name="compiler-error-c2723"></a>编译器错误 C2723

“函数”：“specifier”说明符在函数定义上非法

说明符不能与类声明外部的函数定义同时出现。 仅能对类声明内的成员函数声明指定 `virtual` 说明符。

下面的示例生成 C2723 并显示如何修复它：

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```