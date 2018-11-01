---
title: 编译器错误 C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: 4b99578ed40b4ff70f3606840198b7062083ca83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667034"
---
# <a name="compiler-error-c3671"></a>编译器错误 C3671

function_1： 函数不重写 function_2

使用显式重写语法时，编译器将生成错误，如果未重写函数。  请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C3671。

```
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