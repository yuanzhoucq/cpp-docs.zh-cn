---
title: 编译器错误 C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: 1debe431711681a98b9472c85864d84373ec42d6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775993"
---
# <a name="compiler-error-c3071"></a>编译器错误 C3071

运算符“operator”只能应用于 ref 类或值类型实例中

不能在本机类型上使用 CLR 运算符。 可以在 ref 类或 ref 结构（值类型）上使用运算符，但不可在本机类型（如 int）或本机类型的别名（如 System::Int32）上使用。 这些类型不能从 C++ 代码中以引用本机变量的方式进行装箱，因此无法使用此运算符。

有关详细信息，请参阅[跟踪引用运算符](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3071。

```
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```