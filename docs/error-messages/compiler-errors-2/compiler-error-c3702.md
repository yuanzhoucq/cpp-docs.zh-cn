---
title: 编译器错误 C3702
ms.date: 11/04/2016
f1_keywords:
- C3702
helpviewer_keywords:
- C3702
ms.assetid: 14fcc20e-4404-45d7-be54-e4f09332fa5a
ms.openlocfilehash: 5f9a3509dfe47f2d6d410a05409a28885983cd7a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758003"
---
# <a name="compiler-error-c3702"></a>编译器错误 C3702

"function"： COM 事件需要 ATL

尝试使用 COM 事件，但不包括必要的 ATL 标头文件。

下面的示例生成 C3702：

```cpp
// C3702.cpp
// uncomment the following line to resolve
// #define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name=idid, uuid="12341234-1234-1234-1234-123412341234")];

[object]
__interface IEvents : IUnknown
{
   HRESULT event1([in] int i);
};

[dual]
__interface IBase
{
   HRESULT fireEvents();
};

[coclass, event_source(com)]
class CEventSrc : public IBase
{
   public:
   __event __interface IEvents;

   HRESULT fireEvents()
   {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};   // C3702

int main() {
}
```
