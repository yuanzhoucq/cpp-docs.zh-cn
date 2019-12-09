---
title: 编译器错误 C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 1d3078614ff6818dd4185b3bd5ed2f49413db16f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755949"
---
# <a name="compiler-error-c3609"></a>编译器错误 C3609

“成员”：密封的或最终函数必须是虚拟函数

仅对标记为 `virtual`的类、结构或成员函数允许[密封](../../extensions/sealed-cpp-component-extensions.md)关键字和[final](../../cpp/final-specifier.md)关键字。

以下示例生成 C3609：

```cpp
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
