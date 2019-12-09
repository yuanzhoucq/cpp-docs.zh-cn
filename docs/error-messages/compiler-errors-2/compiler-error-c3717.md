---
title: 编译器错误 C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: cd9a97f1b0d9c9eecfa6a42f735f21a42fd846e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753232"
---
# <a name="compiler-error-c3717"></a>编译器错误 C3717

"method"：不能定义激发事件的方法

你声明了一个包含实现的事件方法。 [__Event](../../cpp/event.md)方法声明不能有定义。 若要修复此错误，请确保没有事件方法声明具有定义。 例如，在下面的代码中，从 `event1` 声明中删除注释所指示的函数体。

下面的示例生成 C3717：

```cpp
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```
