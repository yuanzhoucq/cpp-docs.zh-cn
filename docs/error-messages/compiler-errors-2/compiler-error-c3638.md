---
title: 编译器错误 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 8b1ef7f4cb38653f0ccdfae5684eb2907a735af7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486881"
---
# <a name="compiler-error-c3638"></a>编译器错误 C3638

operator： 标准装箱和取消装箱转换运算符不能重新定义

编译器会定义转换运算符为每个托管类来支持隐式装箱。 此运算符不能重新定义。

有关详细信息，请参阅[隐式装箱](../../windows/boxing-cpp-component-extensions.md)。

下面的示例生成 C3638:

```
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