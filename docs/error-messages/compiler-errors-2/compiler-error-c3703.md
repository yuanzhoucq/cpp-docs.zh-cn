---
title: 编译器错误 C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 1071623c8dbaef52a6a391d8858e7502de9c74b4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757990"
---
# <a name="compiler-error-c3703"></a>编译器错误 C3703

"事件处理程序"：事件处理程序方法必须具有与源 "事件" 相同的存储类

[事件](../../cpp/event-handling.md)具有与它挂钩到的事件处理程序不同的存储类。 例如，如果事件处理程序是静态成员函数，并且事件不是静态的，则会发生此错误。 若要修复此错误，请为事件和事件处理程序指定相同的存储类。

下面的示例生成 C3703：

```cpp
// C3703.cpp
// C3703 expected
#include <stdio.h>

[event_source(type=native)]
class CEventSrc {
public:
   __event static void MyEvent();
};

[event_receiver(type=native)]
class CEventHandler {
public:
   // delete the following line to resolve
   void MyHandler() {}

   // try the following line instead
   // static void MyHandler() {}

   void HookIt(CEventSrc* pSource) {
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }

   void UnhookIt(CEventSrc* pSource) {
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }
};

int main() {
   CEventSrc src;
   CEventHandler hnd;

   hnd.HookIt(&src);
   __raise src.MyEvent();
   hnd.UnhookIt(&src);
}
```
