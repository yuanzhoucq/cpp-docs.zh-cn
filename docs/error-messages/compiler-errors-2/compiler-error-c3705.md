---
title: 编译器错误 C3705 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3705
dev_langs:
- C++
helpviewer_keywords:
- C3705
ms.assetid: 8361017d-5782-4214-a9d7-e9825fd29bc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4c141a7f2cabda7b8fd5f4f15cf731cd1246686
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113729"
---
# <a name="compiler-error-c3705"></a>编译器错误 C3705

function： 找不到事件接口

必须定义要使用 COM 事件的事件接口。 请注意，`#include`行下面的示例中所示的 ATL 标头文件是使用 COM 事件所必需的。 若要解决此错误，请取消注释的定义`IEvents`示例代码中的接口。

下面的示例生成 C3705:

```
// C3705.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following 4 lines to resolve.
// [object, uuid("00000000-0000-0000-0000-000000000003")]
// __interface IEvents : IUnknown {
//    HRESULT event1([in] int i);
// };

[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid("00000000-0000-0000-0000-000000000002")]
class CEventSrc : public IBase {
public:
   __event __interface IEvents;   // C3705 uncomment IEvents to resolve
   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```