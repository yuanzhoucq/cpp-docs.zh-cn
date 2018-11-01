---
title: 编译器错误 C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 9bfdf8b26ab599ef1a28483af7ebc28f0dbc1912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441868"
---
# <a name="compiler-error-c3714"></a>编译器错误 C3714

method： 事件处理程序方法必须具有相同的调用约定为源 method

定义未使用相同的调用约定作为源事件方法的事件处理程序方法。 若要修复此错误，为事件处理程序方法提供源事件方法的相同调用的约定。 例如，以下代码中进行的调用约定`handler1`并`event1`匹配 ([__cdecl](../../cpp/cdecl.md)或[__stdcall](../../cpp/stdcall.md)或其他人)。 删除从两个声明调用约定关键字还将解决该问题，并会导致`event1`并`handler1`默认为[thiscall](../../cpp/thiscall.md)调用约定。 请参阅[调用约定](../../cpp/calling-conventions.md)有关详细信息。

下面的示例生成 C3714:

```
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```