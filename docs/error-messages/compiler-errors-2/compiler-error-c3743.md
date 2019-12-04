---
title: 编译器错误 C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: c0e2082dc87c6236aa11dd3094d056b0024dfc2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752465"
---
# <a name="compiler-error-c3743"></a>编译器错误 C3743

当 event_receiver 的 "layout_dependent" 参数为 true 时，只能挂钩/解除挂钩整个接口

根据传递给[event_receiver](../../windows/event-receiver.md)类中的 `layout_dependent` 参数的值， [__unhook](../../cpp/unhook.md)函数所采用的参数数量不同。

下面的示例生成 C3743：

```cpp
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```
