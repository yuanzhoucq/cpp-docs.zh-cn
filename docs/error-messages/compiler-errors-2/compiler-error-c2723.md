---
title: 编译器错误 C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: f723fcc0a3d9626f01f2059a3d9363801221bca0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216045"
---
# <a name="compiler-error-c2723"></a>编译器错误 C2723

“函数”：“specifier”说明符在函数定义上非法

说明符不能与类声明外部的函数定义同时出现。 **`virtual`** 只能在类声明中的成员函数声明上指定说明符。

下面的示例生成 C2723 并显示如何修复它：

```cpp
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```
