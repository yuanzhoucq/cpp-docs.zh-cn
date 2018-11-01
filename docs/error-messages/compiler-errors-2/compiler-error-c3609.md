---
title: 编译器错误 C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 5572f39082e2dcd8746bb464595c5c00e2f77356
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556437"
---
# <a name="compiler-error-c3609"></a>编译器错误 C3609

“成员”：密封的或最终函数必须是虚拟函数

[密封](../../windows/sealed-cpp-component-extensions.md)并[最终](../../cpp/final-specifier.md)关键字只能在类、 结构或成员函数标记为`virtual`。

以下示例生成 C3609：

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
