---
title: 编译器错误 C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447263"
---
# <a name="compiler-error-c2803"></a>编译器错误 C2803

operator operator 必须具有至少一个类类型的形参

重载的运算符缺少类类型的参数。

您需要通过引用（不是使用指针，而是使用引用）或值至少传递一个参数，才能够编写“a < b”（a 和 b 均为类 A 类型）。

如果这两个参数都是指针，它将是纯比较的指针地址，且不会将用户定义的转换。

下面的示例生成 C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```