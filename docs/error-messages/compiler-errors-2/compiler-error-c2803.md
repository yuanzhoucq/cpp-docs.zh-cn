---
title: 编译器错误 C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d39f737ba02f3fa9c9d5f61594ddf730db6739a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760655"
---
# <a name="compiler-error-c2803"></a>编译器错误 C2803

"operator operator" 必须至少有一个类类型的形参

重载运算符缺少类类型的参数。

需要通过引用传递至少一个参数（不使用指针，而不是引用）或通过值来编写 "a < b" （a 和 b 类型为类 A）。

如果这两个参数都是指针，则它将是指针地址的纯粹比较，并且不会使用用户定义的转换。

下面的示例生成 C2803：

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
