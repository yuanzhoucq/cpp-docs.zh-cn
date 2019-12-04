---
title: 编译器错误 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: f8d67ac0ff6a1fa5d9efbb8d85747ff94d75c648
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742491"
---
# <a name="compiler-error-c3638"></a>编译器错误 C3638

"operator"：不能重新定义标准装箱和取消装箱转换运算符

编译器为每个托管类定义一个转换运算符，以支持隐式装箱。 不能重新定义此运算符。

有关详细信息，请参阅[隐式装箱](../../extensions/boxing-cpp-component-extensions.md)。

下面的示例生成 C3638：

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
