---
title: 编译器错误 C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 33bb248faf946c39543de4a14a44e2ebbda49880
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776738"
---
# <a name="compiler-error-c3638"></a>编译器错误 C3638

operator： 标准装箱和取消装箱转换运算符不能重新定义

编译器会定义转换运算符为每个托管类来支持隐式装箱。 此运算符不能重新定义。

有关详细信息，请参阅[隐式装箱](../../extensions/boxing-cpp-component-extensions.md)。

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