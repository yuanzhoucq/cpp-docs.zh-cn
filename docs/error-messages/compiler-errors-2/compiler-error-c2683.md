---
title: 编译器错误 C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: cd629b093bdc3992a8ea69f498b1e1cdab1b8826
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214628"
---
# <a name="compiler-error-c2683"></a>编译器错误 C2683

"cast"： "type" 不是多态类型

不能使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)从非多态类（不带虚函数的类）进行转换。

您可以使用[static_cast](../../cpp/static-cast-operator.md)来执行非多态类型的转换。 但是，不 **`static_cast`** 执行运行时检查。

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
