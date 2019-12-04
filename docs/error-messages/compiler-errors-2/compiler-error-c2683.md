---
title: 编译器错误 C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 8526dc1fe3cacc872aa91ca058677d15318fd703
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760265"
---
# <a name="compiler-error-c2683"></a>编译器错误 C2683

"cast"： "type" 不是多态类型

不能使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)从非多态类（不带虚函数的类）进行转换。

您可以使用[static_cast](../../cpp/static-cast-operator.md)来执行非多态类型的转换。 但 `static_cast` 不执行运行时检查。

下面的示例生成 C2683：

```cpp
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```
