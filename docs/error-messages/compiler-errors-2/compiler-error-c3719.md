---
title: 编译器错误 C3719 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3719
dev_langs:
- C++
helpviewer_keywords:
- C3719
ms.assetid: d0d59d4e-babb-4480-9ef7-70cf1a28165c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04761008bd7dcdfa9ecb8dc1d6c24be4a67a6360
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047858"
---
# <a name="compiler-error-c3719"></a>编译器错误 C3719

interface： 接口基于的事件源只用于 COM 事件

声明中的非 COM 上下文的接口。

下面的示例生成 C3719:

```
// C3719a.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];

[object]
__interface I {
   HRESULT func1();
};

[event_source(native), coclass]
struct A {
   __event __interface I;   // C3719

   // try the following line instead
   // __event func2();
};

int main() {
}
```

若要修复此错误，应用[对象](../../windows/object-cpp.md)，[组件类](../../windows/coclass.md)， [event_source](../../windows/event-source.md)，以及[event_receiver](../../windows/event-receiver.md)属性相应地进行使用接口 COM 类的类。 例如：

```
// C3719b.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="xx")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f();
};

[coclass, event_source(com) , uuid("00000000-0000-0000-0000-000000000002")]
struct MyStruct {
   __event __interface I;
};

[event_receiver(com)]
struct MyStruct2 {
   void f() {
   }
   MyStruct2(I* pB) {
      __hook(&I::f, pB, &MyStruct2::f);
   }
};

int main()
{
}
```