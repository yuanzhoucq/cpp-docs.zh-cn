---
title: 编译器错误 C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: af30ccc4a71c51d042d6f7807a648a1eef066a70
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742660"
---
# <a name="compiler-error-c2970"></a>编译器错误 C2970

"class"：模板参数 "param"： "arg"：涉及带有内部链接的对象的表达式不能用作非类型参数

不能将静态变量的名称或地址用作模板参数。 模板类需要可以在编译时计算的常量值。

下面的示例生成 C2970：

```cpp
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```
