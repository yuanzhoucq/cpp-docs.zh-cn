---
title: "编译器错误 C3714 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3714"
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method”: 事件处理程序方法必须有与源“method”相同的调用约定  
  
 您定义的事件处理程序方法与源事件方法使用的调用约定不同。  若要修复此错误，请给予事件处理程序方法与源事件方法的调用约定相同的调用约定。  例如，在下面的代码中，使 `handler1` 和 `event1` 的调用约定匹配（[\_\_cdecl](../../cpp/cdecl.md)、[\_\_stdcall](../../cpp/stdcall.md) 或其他）。  从两个声明中移除调用约定关键字也能解决该问题，同时使 `event1` 和 `handler1` 采用默认的 [thiscall](../../cpp/thiscall.md) 调用约定。  有关更多信息，请参见[调用约定](../../cpp/calling-conventions.md)。  
  
 下面的示例生成 C3714：  
  
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