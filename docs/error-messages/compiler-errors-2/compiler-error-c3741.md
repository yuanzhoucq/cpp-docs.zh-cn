---
title: 编译器错误 C3741 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3741
dev_langs:
- C++
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 531b2765bb829a6278bf2d1ca663733f6279b1b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106891"
---
# <a name="compiler-error-c3741"></a>编译器错误 C3741

class： 必须是组件类当 event_receiver 的 layout_dependent 参数 = true

当`layout_dependent=true`有关[event_receiver](../../windows/event-receiver.md)类，则此类还必须具有[组件类](../../windows/coclass.md)属性。

下面的示例生成 C3741

```
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```