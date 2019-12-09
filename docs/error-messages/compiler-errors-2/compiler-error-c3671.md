---
title: 编译器错误 C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: 030a6acb19c0907956d2a5b833b683821591e5c5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758107"
---
# <a name="compiler-error-c3671"></a>编译器错误 C3671

"function_1"：函数没有重写 "function_2"

使用显式 override 语法时，如果未重写函数，编译器将生成错误。  有关详细信息，请参阅[显式重写](../../extensions/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3671。

```cpp
// C3671.cpp
// compile with: /clr /c
ref struct S {
   virtual void f();
};

ref struct S1 : S {
   virtual void f(int) new sealed = S::f;   // C3671
   virtual void f() new sealed = S::f;
};
```
