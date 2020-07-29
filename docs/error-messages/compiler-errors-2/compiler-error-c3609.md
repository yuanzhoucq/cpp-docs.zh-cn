---
title: 编译器错误 C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 2eff238aed756c9f056da9a1b9a70fca9de24fa3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230800"
---
# <a name="compiler-error-c3609"></a>编译器错误 C3609

“成员”：密封的或最终函数必须是虚拟函数

仅对标记为的类、结构或成员函数允许使用[sealed](../../extensions/sealed-cpp-component-extensions.md)和[final](../../cpp/final-specifier.md)关键字 **`virtual`** 。

以下示例生成 C3609：

```cpp
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
