---
title: 编译器错误 C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753323"
---
# <a name="compiler-error-c3714"></a>编译器错误 C3714

"method"：事件处理程序方法必须具有与源 "method" 相同的调用约定

您定义了一个事件处理程序方法，该方法不使用与源事件方法相同的调用约定。 若要修复此错误，请为事件处理程序方法指定与源事件方法相同的调用约定。 例如，在下面的代码中，`handler1` 和 `event1` 匹配（[__cdecl](../../cpp/cdecl.md)或[__stdcall](../../cpp/stdcall.md)或其他内容）进行调用约定。 从这两个声明中删除调用约定关键字还能解决该问题，并导致 `event1` 和 `handler1` 默认为[thiscall](../../cpp/thiscall.md)调用约定。 有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

下面的示例生成 C3714：

```cpp
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
