---
title: 编译器错误 C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 5601dd2f510e4322e67f49478eefce795312e380
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494170"
---
# <a name="compiler-error-c3651"></a>编译器错误 C3651

member： 不能用作显式重写，必须是基类的成员

指定显式重写，但不是基类型的类型中被重写函数时。

有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。

下面的示例生成 C3651:

```
// C3651.cpp
// compile with: /clr /c
ref class C {
public:
   virtual void func2();
};

ref class Other {
public:
   virtual void func();
};

ref class D : public C {
public:
   virtual void func() new sealed = Other::func;   // C3651
   virtual void func2() new sealed = C::func2;   // OK
};
```