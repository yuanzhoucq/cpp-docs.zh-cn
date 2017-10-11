---
title: "编译器错误 C3714 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3714
dev_langs:
- C++
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7d58e06d99975fd4ccff9ea4bace755ff1d758cb
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3714"></a>编译器错误 C3714
method： 事件处理程序方法必须具有相同的调用约定为源 method  
  
 您定义未使用的相同的调用约定作为源事件方法的事件处理程序方法。 若要修复此错误，赋予事件处理程序方法与源事件方法的相同的调用约定。 例如，在下面的代码中，进行的调用约定`handler1`和`event1`匹配 ([__cdecl](../../cpp/cdecl.md)或[__stdcall](../../cpp/stdcall.md)或其他人)。 删除调用约定关键字从这两个声明将还解决问题，并导致`event1`和`handler1`默认为[thiscall](../../cpp/thiscall.md)调用约定。 请参阅[调用约定](../../cpp/calling-conventions.md)有关详细信息。  
  
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
