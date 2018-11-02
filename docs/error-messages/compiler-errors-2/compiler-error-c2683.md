---
title: 编译器错误 C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 49e4897ad5db866aa1ca42589859bedff12718df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625151"
---
# <a name="compiler-error-c2683"></a>编译器错误 C2683

cast： 不是多态类型 type。

不能使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)将从非多态类 （具有没有虚函数的类）。

可以使用[static_cast](../../cpp/static-cast-operator.md)来执行非多态类型的转换。 但是，`static_cast`不会执行运行时检查。

下面的示例生成 C2683:

```
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```