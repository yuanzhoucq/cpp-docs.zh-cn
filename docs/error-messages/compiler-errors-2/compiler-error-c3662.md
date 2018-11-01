---
title: 编译器错误 C3662
ms.date: 11/04/2016
f1_keywords:
- C3662
helpviewer_keywords:
- C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
ms.openlocfilehash: c8f2252c05e3e264740004f4126c7557f30b126a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657322"
---
# <a name="compiler-error-c3662"></a>编译器错误 C3662

“member”：重写说明符“specifier”只允许在托管类或 WinRT 类的成员函数上使用

不允许在本机类型的成员上使用重写说明符。

有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3662。

```
// C3662.cpp
// compile with: /clr /c
struct S {
   virtual void f();
};

struct S1 : S {
   virtual void f() new;   // C3662
};

ref struct T {
   virtual void f();
};

ref struct T1 : T {
   virtual void f() new;   // OK
};
```